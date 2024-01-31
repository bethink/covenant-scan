<template>
  <div class="layout">
    <a-breadcrumb class="breadcrumb">
      <a-breadcrumb-item>
        <router-link to="/">Home</router-link>
      </a-breadcrumb-item>
      <a-breadcrumb-item>Transaction List</a-breadcrumb-item>
    </a-breadcrumb>
    <div class="card txs">
      <p class="title">Transaction List</p>
      <p>The current number of transactions produced is {{latestTxCount}}</p>
      <a-table
        :columns="columns"
        :rowKey="record => record.height"
        :dataSource="data"
        :pagination="pagination"
        :loading="loading"
        @change="handleTableChange"
        size="middle"
      >
        <span slot="height" slot-scope="text">#{{text}}</span>
        <span slot="cutHash" slot-scope="text">
          <hash-tip :hash="text" :cutLength="20"/>
        </span>
        <span slot="toHash" slot-scope="text">
          <router-link :to="'/tx/' + text">
            <hash-tip :hash="text" :cutLength="20"/>
          </router-link>
        </span>
        <span slot="raw" slot-scope="tx">
          <raw-tx :tx="tx"/>
        </span>
        <span slot="date" slot-scope="text">{{formatDate(text)}}</span>
      </a-table>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import { State, namespace } from 'vuex-class'
import moment from 'moment'
import HashTip from '@/components/HashTip.vue'
import RawTx from '@/components/RawTx.vue'

@Component({
  components: {
    HashTip,
    RawTx,
  },
})
export default class Txs extends Vue {
  @State('bp') bpState
  @namespace('bp').Getter latestTxCount

  // table columns
  private columns = [
    {
      title: 'Block Height',
      dataIndex: 'block_height',
      scopedSlots: { customRender: 'height' },
    },
    {
      title: 'Address',
      dataIndex: 'address',
      scopedSlots: { customRender: 'cutHash' },
    },
    {
      title: 'Hash',
      dataIndex: 'hash',
      scopedSlots: { customRender: 'toHash' },
    },

    {
      title: 'Transaction Type',
      dataIndex: 'type',
    },
    {
      title: 'Transaction Raw Data',
      dataIndex: 'tx',
      scopedSlots: { customRender: 'raw' },
    },
    {
      title: 'Time',
      dataIndex: 'timestamp_human',
      scopedSlots: { customRender: 'date' },
    },
  ]

  data = []
  pagination = {
    total: 0,
    pageSize: 16,
    page: 1,
    current: 1,
  }
  loading = false

  // lifecycle hook
  mounted() {
    this.$store.dispatch('bp/connectBP').then(() => this.fetchData(1))
  }

  handleTableChange(pagination: any) {
    console.log(pagination)
    const current: number = pagination.current
    this.pagination.current = current
    this.fetchData(current)
  }

  // methods
  formatDate(date) {
    return moment(date).format('YYYY-MM-DD HH:mm:ss')
  }

  // async
  async fetchData(page = this.pagination.current) {
    this.loading = true
    try {
      let result = await this.$store.dispatch('bp/getTxs', {
        page: page,
        size: this.pagination.pageSize,
      })
      this.data = result.transactions
      this.pagination.total = result.pagination.total
      this.loading = false
    } catch (error) {
      console.error(error)
    }
  }
}
</script>

<style lang="scss" scoped>
.layout {
  margin: 0 auto;
  padding: 20px 15px 40px;
  width: 1200px;
  max-width: 100%;
  min-height: 55vh;
  color: #252728;
}
.breadcrumb {
  margin-bottom: 15px;
}
.raw-tx {
  font-size: 12px;
  .row {
    .label {
      color: #888;
      margin-right: 5px;
    }
  }
}
</style>
