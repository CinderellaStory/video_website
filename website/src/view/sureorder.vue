<template>
 <div class="sureorder">
    <Mheader></Mheader>
    <h1 class="mw">确认订单</h1>
    <div class="mw content">
        <div class="sureorder-box">
            <p class="order-times">下单时间：<span>2018-08-08 08:08</span></p>
            <div class="course-item">
              <ul>
                <li v-for="(item,index) in items" :key="index">
                  <div class="course-img fl"><img src="../assets/web.png" alt=""></div>
                  <div class="course-info fl">
                    <p class="course-name">{{item.courseneme}}</p>
                    <p class="teachers-name">{{item.teachersneme}}</p>
                    <p class="videos-times">{{item.videostimes}}</p>
                  </div>
                  <div class="course-price fl">￥{{item.courseprice}}</div>
                </li>
              </ul>
            </div>
            <div class="pay-box ov">
              <div class="fl payinfo">
                <p class="number">共1件课程</p> 
                <p class="amount">商品总金额：<span>￥299.99</span></p>
              </div>
              <div class="fl wechat">
                <button @click="wechatpay">微信支付</button>
              </div>
              <div class="fr alipay">
                <button @click="alipay">支付宝支付</button>
              </div>
            </div>
              <p class="notice"><i class="iconfont icon-gantanhao"></i>请在22小时30分钟 以内支付完成，如未完成此订单将自动关闭。需重新购买！</p>
        </div>
    </div>
    <div class="wechat-dialog" v-show="show">
      <div class="dialog_bg"></div>
      <div class="wechat-dialog-container">
        <div class="title">
          {{wechat}}<i class="iconfont icon-delete" @click="CloseDialog"></i>
        </div>
        <div class="wechat-box">
          <img src="../assets/wechat.jpg" alt="">
        </div>
        <p>微信支付</p>
      </div>
    </div>
    <div class="alipay-dialog" v-show="alipayshow">
      <div class="dialog_bg"></div>
      <div class="wechat-dialog-container">
        <div class="title">
          {{wechat}}<i class="iconfont icon-delete" @click="CloseDialog"></i>
        </div>
        <div class="wechat-box">
          <img src="../assets/wechat.jpg" alt="">
        </div>
        <p>支付宝支付</p>
      </div>
    </div>
 </div>
</template>

<script type="text/javascript">
import Mheader from '@/components/Mheader'

  export default {
   data() {
     return {
       show:false,
       alipayshow:false,
       wechat:'微信付款',
       items:[
        {
           courseneme:'全网最热Python3入门+进阶 更快上手实际开发',
           teachersneme:'请叫我小任性',
           videostimes:'视频时长：一个小时20分',
           courseprice:333.33
        },
        {
           courseneme:'全网最热Python3入门+进阶 更快上手实际开发',
           teachersneme:'请叫我小任性',
           videostimes:'视频时长：一个小时20分',
           courseprice:333.33
        }
       ]
      }
  },
  methods:{
    wechatpay(){
      this.show = true;
    },
    alipay(){
      this.alipayshow = true;
    },
     CloseDialog(){
        this.show = false;
        this.alipayshow = false;
      }
  },
   components: {
     Mheader
   }
 }
</script>

<style scoped lang="less">
.mw{
    width: 1000px;
    margin: 45px auto;
}
h1{
  text-align: left;
}
i{
  margin-right: 6px;
  vertical-align: middle;
}
button{
  border: none;
  color: #fff;
  font-size: 12px;
  width: 160px;
  height: 34px;
  line-height: 34px;
  text-align: center;
  border-radius: 4px;
  cursor: pointer;
}
.content{
  background: #fff;
  box-shadow: 0 2px 8px 2px rgba(0, 0, 0, 0.1);
  padding: 20px 30px 60px 30px;
  }

  .sureorder-box{
    .order-times{
      text-align: left;
      margin-bottom: 16px;
    }
    .course-item{
      ul{
        li{
          overflow: hidden;
          background: #f3f5f7;
          margin-top: 20px;
          padding: 20px;
          .course-img{
            img{
              width: 160px;
              height: 90px;
            }
          }
          .course-info{
            width: 60%;
            margin-left: 20px;
            text-align: left;
            font-size: 14px;
            color: #333;
            p{
              line-height: 30px;
              &.course-name{
                font-weight: bold;
                font-size: 15px;
              }
            }
          }
          .course-price{
            line-height: 90px;
            color: red;
            font-size: 16px;
          }
        }
      }
    }
    .pay-box{
        display: flex;
        width: 100%;
        align-items: center;
      .payinfo{
        width: 100%;
        margin: 20px 0 10px;
        p{
        text-align: left;
        line-height: 30px;
        }
        .amount{
          span{
            color: red;
            font-weight: bold;
            font-size: 16px;
          }
        }
      }
      .wechat{
        width: 50%;
        button{
          background: #00C800;
        }
      }
      .alipay{
        text-align: right;
        button{
          background: #00AAEE;
        }
      }
    }
    .notice{
      color: #FF9800;
      font-size: 12px;
      float: right;
    }
  }
  .wechat-dialog{
    .dialog_bg{
      background: #000;
      opacity: 0.75;
      position: fixed;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
    }
    .wechat-dialog-container{
      text-align: center;
      width: 420px;
      padding-bottom: 30px;
      background: #fff;
      top: 30%;
      border-radius: 10px;
      left: 38%;
      position: absolute;
      box-shadow: 0 2px 8px 2px rgba(0, 0, 0, 0.1);
      .icon-delete{
        position: absolute;
        right: 10px;
        cursor: pointer;
        top: 10px;
    }
     .title{
          border-radius: 10px 10px 0 0;
          padding: 14px 20px; 
          color: #fff;
          position: relative;
          text-align: center;
          background: #6CB6FD;
          border-bottom: 1px solid #3E95E5;
          padding-bottom: 10px;
      }
      p{
        font-size: 20px;
      }
    }
  }
  .alipay-dialog{
    .dialog_bg{
      background: #000;
      opacity: 0.75;
      position: fixed;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
    }
    .wechat-dialog-container{
      text-align: center;
      width: 420px;
      padding-bottom: 30px;
      background: #fff;
      top: 30%;
      border-radius: 10px;
      left: 38%;
      position: absolute;
      box-shadow: 0 2px 8px 2px rgba(0, 0, 0, 0.1);
      .icon-delete{
        position: absolute;
        right: 10px;
        cursor: pointer;
        top: 10px;
    }
     .title{
          border-radius: 10px 10px 0 0;
          padding: 14px 20px; 
          color: #fff;
          position: relative;
          text-align: center;
          background: #6CB6FD;
          border-bottom: 1px solid #3E95E5;
          padding-bottom: 10px;
      }
      p{
        font-size: 20px;
      }
    }
  }
</style>
