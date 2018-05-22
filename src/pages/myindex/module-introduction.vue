<template>
  <section id="module-introduction">
    <div class="container">
       <el-row>
        <el-col :span="15" class="span1">
          <el-row>
            <el-col :span="3"><h4>中消<i>百科</i></h4></el-col>
            <el-col :span="19">
              <ul class="navList-ul">
                <li v-for="item in navLists" class="col" @click="selected(item.name,item.id)" :class="{'cur': activeName == item.name}">{{item.name}}</li>
              </ul>
            </el-col>
            <el-col :span="2">
              <a href="/article-encyclop-1.html" class="more" target="_blank">更多>></a>
              <!-- <router-link :to="navlist.newsurl" class="text-more"></router-link> -->
            </el-col>
          </el-row>
          <el-row>
          <ul class="list marginTop15" v-if="lists">
            <li v-for="item in lists" class="item listLeft">
              <el-row>
                <el-col :span="6" style="display: table-cell;vertical-align: middle;">
                  <!-- <img src="./images/module-introduction-img002.png"> -->
                  <img :src="item.thumbnail" class="img-responsive" :onerror="defaultImg"/>
                </el-col>
                <el-col :span="17" style="margin-left: 15px;">
                  <a :href="item.link_to" class="item-title" target="_blank">{{item.title}}</a>
                  <p class="newContent" v-if="item.remarks">
                    <!-- {{item.fold ? maxSlice(item.remarks) : item.remarks}} -->
                    {{maxSlice(item.remarks)}} 
                  </p>
                  <el-row>
                    <el-col :span="18" class="keyWord">{{item.meta_keywords}}</el-col>
                    <el-col :span="6" class="right">
                      <span class="item-date">{{item.created.substring(0,4)}}/{{item.created.substring(5,7)}}/{{item.created.substring(8, 10)}}</span>
                    </el-col>
                  </el-row>
                </el-col>
              </el-row>
            </li>
          </ul>
          </el-row>
        </el-col>
        <el-col :span="8">
          <el-row class="content">
            <div class="redLine"></div>
            <h4 class="title-h4">招标<i>公示</i></h4>
            <ul class="list" v-if="tenderLists">
              <li v-for="(item,index) in tenderLists" class="item" :class="{hasClass:index <=2}">
                <span style="font-size: 48px;line-height: 20px;">&middot;</span>&nbsp;
                <a :href="item.link_to" class="item-title" target="_blank">{{item.title}}</a>
                <span class="item-date">{{item.item_date.substring(5,7)}}/{{item.item_date.substring(8, 10)}}</span>
              </li>
            </ul>
          </el-row>
          <el-row style="margin-top: 30px;">
            <!-- <router-link :to="navlist.ruleurl" class="text-more">更多>></router-link> :href="baseUrl+'/'+pages/encyclop/encyclop-save/encyclop-save.html"-->
            <div class="redLine"></div>
            <h4 class="title-h4" style="background-color: #fff;">中消<i>救援</i></h4>
            <a :span="24" class="saveZx" href="/article-encyclopSave-1.html#/"><img src="./images/module-introduction-img001.png"></a>
          </el-row>
        </el-col>
      </el-row>
    </div>
  </section>
</template>

<script>
  export default {
    name: 'module-introduction',
    data: function () {
      return {
        maxLength:142,
        activeId:'5,11,14,44,45,47',
        activeName:'全部',
        lists:'',
        newslists: '',
        navLists:[
        {
          id: '5,11,14,44,45,47',
          name: '全部'
        },
        {
          id: '11',
          name: '政策法规'
        },
        {
          id: '5',
          name: '热点新闻'
        },
        {
          id: '14',
          name: '消防百科'
        },
        {
          id: '44',
          name: '专家解读'
        },
        {
          id: '45',
          name: '展会资讯'
        },
        {
          id: '47',
          name: '消防科技'
        }
      ],
      tenderLists: [
          {
            location:'广东',
            title:'新塘镇垃圾中转站点改造工程',
            link_to:'http://www.xfbid.com/bid/detail/xfbid-13-25168827.html',
            id:'111',
            item_date:'2018-05-21'
          },
          {
            location:'广东',
            title:'广东省佛山市消防器材装备采购',
            link_to:'http://www.xfbid.com/bid/detail/xfbid-13-25168709.html',
            id:'111',
            item_date:'2018-05-21'
          },
          {
            location:'山东',
            title:'威尼斯东区建设项目室外管网工程施工招标公告',
            link_to:'http://www.xfbid.com/bid/detail/xfbid-13-25150608.html',
            id:'111',
            item_date:'2018-05-21'
          },
          {
            location:'辽宁',
            title:'古生物博物馆监控改造与消防维修工程招标公告',
            link_to:'http://www.xfbid.com/bid/detail/xfbid-13-25168415.html',
            id:'111',
            item_date:'2018-05-19'
          },
          {
            location:'山东',
            title:'国检董家口临时通关中心实验室改造工程项目招标公告',
            link_to:'http://www.xfbid.com/bid/detail/xfbid-13-25168209.html',
            id:'111',
            item_date:'2018-05-19'
          },
          {
            location:'吉林',
            title:'乌鲁木齐经济技术开发区（头屯河区）2018年度第31期询价采购公告',
            link_to:'http://www.xfbid.com/bid/detail/xfbid-13-25168094.html',
            id:'111',
            item_date:'2018-05-19'
          },
          {
            location:'北京',
            title:'开发区消防大队青岛经济技术开发区消防大队消防车辆、器材装备购置项目公开招标公告',
            link_to:'http://www.xfbid.com/bid/detail/xfbid-13-25167953.html',
            id:'111',
            item_date:'2018-05-19'
          },
          {
            location:'广西',
            title:'北流市新荣镇教学楼工程施工招标公告 项目编号：BLZC2018-G2-0086',
            link_to:'http://www.xfbid.com/bid/detail/xfbid-13-25167448.html',
            id:'111',
            item_date:'2018-05-19'
          },
          {
            location:'广西',
            title:'中鼎誉润工程咨询有限公司横县公安消防大队城西消防站及综合应急救援基地项目岩土工程勘察项目邀请招标公告',
            link_to:'http://www.xfbid.com/bid/detail/xfbid-13-25167392.html',
            id:'111',
            item_date:'2018-05-19'
          }
        ],
        defaultImg:'this.src="' + require('./images/module-introduction-img002.png') + '"'
      }
    },
    mounted () {
      this.get_data()
    },
    methods: {
      maxSlice:function (item) {
        return item.length > this.maxLength ? item.slice(0,this.maxLength) + '...' : item
      },
      get_data: function () {
        this.$api.get('/api', {method: 'querywaterfall', page: 1, pagesize: 4, taxonomyid: this.activeId}, (r) => {
          this.lists = r.data.list
          console.log(this.lists)
        })
        this.$api.get('/api', {method: 'querywaterfall', page: 1, pagesize: 8, taxonomyid: 11}, (r) => {
        this.newslists = r.data.list
        })
      },
      selected: function(item,id) {
      this.activeName = item
      this.activeId = id
      this.get_data()
      }
    }
  }
</script>

<style lang="scss">
  #module-introduction {margin: 70px 0 50px 0;/*height: 830px;*/
    .saveZx{width: 100%;height: 100%;display: inline-block;}
    .navList-ul li{width: 75px;float: left;text-align: center;cursor: pointer;font-size: 14px;
      &.cur{color:#c41335;}
    }
    .navList-ul li:first-child{margin-left: 10px;}
    .moreMuch{color: #cc0033;}
    .marginTop15{margin-top: 30px;
      .right{text-align: right;float: right;
        .item-date{color: #818181;}
      }
    }
    li.listLeft{border-bottom: 1px solid #aaaaaa;height: 200px;
      img{display: block;margin-top: 40px;}
      .img-responsive{padding: 5px;border-radius: 3px; display: table-cell;width: 180px;height: 115px;
        vertical-align: middle;
      }
      .newContent{font-size: 14px;line-height: 25px;height: 100px;overflow: hidden;margin: 0;padding: 0;margin-bottom: 20px;color:#555;}
      .item-title{font-size: 20px;line-height: 50px;overflow: hidden;text-overflow: ellipsis;white-space: nowrap;vertical-align: top;width: 90%;display: inline-block;font-weight: bold;}
      .item-title:hover{color: #cc0033;text-decoration: underline;}
      .keyWord,.item-date{color: #cc0033; overflow: hidden;text-overflow: ellipsis;white-space: nowrap;vertical-align: top;}
    }
    li.listLeft:last-child {
            border-bottom: 0px;
          }
          
    .span1{margin-right: 48px;font-size: 14px;
      .more{color:#c41335;}
      h4{font-size: 20px;line-height: 28px;border-bottom: 3px solid #c41335;width: 85px;text-align: center;margin-top: -6px;}
      a:hover{color: #c41335;}
    }
    i{font-style: normal;color: #cc0033;}
    .redLine{width: 100%;height: 2px;background-color: #cc0033;}
    .title-h3{border-bottom: 3px solid #cc0033;width: 85px;font-size: 18px;text-align: center;margin-bottom: 20px;}
    .title-h4{text-align: center;width: 90px;margin: -15px auto 10px auto;background-color: #f7f6f5;font-size: 18px;line-height: 28px;}
    a:hover span {
      text-decoration: underline;
    }
    .content {
      position: relative;
      padding: 25px 25px 15px 25px;
      background-color: #f7f6f5;

      a:hover {
        text-decoration: underline;
        color: $hot-dark;
      }
      .text-more {
        position: absolute;
        top: 8px;
        right: 10px;
      }
      ul.list {margin-top: 20px;
        & > li.hasClass{color: #c41335;
          a{color: #c41335;}
        }
        & > li.item {
          .item-title {
            display: inline-block;font-size: 14px;
            width: 80%;
            overflow: hidden;
            text-overflow: ellipsis;
            white-space: nowrap;
            vertical-align: top;
          }
         /* &:not(:last-child) {
            margin-bottom: 10px;
          }*/
          
          .item-date {font-size: 14px;
            display: inline-block;
            overflow: hidden;
            float: right;
          }
        }
      }
    }
  }
</style>