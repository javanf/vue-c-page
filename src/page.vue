<template>
  <section class="pagination cf">
    <div class="c-pagination fr"><span class="fl">共{{ pageOption.total }}条记录</span><a class="btn-type-2 ctrl-l fl" href="javascript:;" @click="jumpTo(pageNo - 1 === 0 ? 1 : pageNo - 1)">&nbsp;</a>
      <ul class="fl" v-if="pageNo">
        <template v-if="totalPage <= 6">
          <li class="fl" v-for="i in totalPage"><a class="c-inl" :class="{current: i === pageNo }" @click="jumpTo(i)" href="javascript:;">{{ i }}</a></li>
        </template>
        <template v-else="v-else">
          <template v-if="totalPage - pageNo < 6">
            <li class="fl">……</li>
            <li class="fl" v-for="i in 6"><a class="c-inl" :class="{current: totalPage - 6 + i === pageNo }" @click="jumpTo(totalPage - 6 + i)" href="javascript:;">{{ totalPage - 6 + i }}</a></li>
          </template>
          <template v-else="v-else">
            <template v-if="pageNo === 1 ||　pageNo === 2">
              <li class="fl" v-for="i in 3"><a class="c-inl" :class="{current: i === pageNo }" @click="jumpTo(i)" href="javascript:;">{{ i }}</a></li>
            </template>
            <template v-else="v-else">
              <li class="fl">……</li>
              <li class="fl" v-for="i in 3"><a class="c-inl" :class="{current: pageNo - 2 + i === pageNo }" @click="jumpTo(pageNo - 2 + i)" href="javascript:;">{{ pageNo - 2 + i }}</a></li>
            </template>
            <li class="fl">……</li>
            <li class="fl" v-for="i in 3"><a class="c-inl" :class="{current: totalPage - 3 + i === pageNo }" @click="jumpTo(totalPage - 3 + i)" href="javascript:;">{{ totalPage - 3 + i }}</a></li>
          </template>
        </template>
      </ul><a class="btn-type-2 ctrl-r fl" href="javascript:;" @click="jumpTo(pageNo + 1 > (totalPage || 0) ? pageNo : pageNo + 1)">&nbsp;</a>
      <form class="fl" @submit.prevent="jumpTo(goPageNo)" v-if="totalPage > 1">
        <div class="input-icon fl">
          <input class="tc" type="text" v-model="goPageNo" />
        </div>
        <button class="fl tc btn-type-2" type="submit">跳转</button>
      </form>
    </div>
  </section>
</template>

<script>
	export default {
    name: "CPage",
		props: ['pageOption', 'jumpTo'],
		data () {
			return {
				goPageNo: this.pageOption.pageNo || 1,
			}
		},
		computed :{
			pageNo() {
				return this.pageOption.pageNo || 1
			},
			totalPage() { 
				return this.pageOption.totalPage || 1;
			}
		},
		watch:{
			goPageNo (val) {
				if(!val || val < 1) {
					this.goPageNo = 1;
				}
				if(val > this.totalPage) {
					this.goPageNo = this.totalPage;
				}
			}
		}
	}
</script>

<style lang="scss">
.c-pagination{
	line-height: 32px;
	*{
		padding: 0;
		margin: 0;
		border: 0;
    color: #333;
  }
  .fl{
    float: left;
  }
  a{
    text-decoration: none;
  }
	button{
		width: 55px;
		margin-left: 6px;
  }
	input{
		width: 75px;
		line-height: 20px;
    border: none;
    outline: none;
    text-align: center;
  }
	li{
		margin: 0 3px;
    list-style: none;
		a{
			line-height: 18px;
			width: 18px;
			text-align: center;
      display: inline-block;
      padding: 3px;
      &:hover{
        background-color: #FF7362;
		    color: #fff;
        border-radius: 50%;
      }
    }
  }
	.btn-type-2, .input-icon{
		line-height: 30px;
		border: 1px solid #d0d0d0;
		font-size: inherit;
		border-radius: 3px;
  }
	.ctrl-l, .ctrl-r{
		width: 28px;
		background-image: url('./assets/arrow-r.svg');
    background-size: 13px 13px;
		background-position: center center;
		background-repeat: no-repeat;
  }
	.ctrl-l{
		margin-left: 16px;
  }
	.ctrl-l{
		transform: rotate(180deg);
  }
  .input-icon{
    margin-left: 6px;
  }
	.current{
		border-radius: 50%;
		background-color: #FF7362;
		color: #fff;
  }
}
</style>