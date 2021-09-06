<!--教师段主页右侧的课程详情-->
<template>
<div id="courseDetail" style="border:2px solid #EBEBEB;border-radius: 15px;background-color: #FFFFFF">
<!--  显示解题单元、班级、邀请码、按钮-->
  <Row justify="start">
    <Col span="1">
    </Col>
    <Col span="13">
      <br>
      <h1>{{courseDetail.courseName}}</h1>
      <br>
      <h2>{{courseDetail.className}} 邀请码{{courseDetail.inviteCode}}</h2>
    </Col>
    <Col span="1">
    </Col>
    <Col span="4">
      <br>
      <br>
      <Button style="background-color: #9D81FF;width:60%;height:50%" size="large" >GO</Button>
    </Col>
  </Row>
<!--分界线-->
  <Row>
    <Col span="1"></Col>
    <br>
    <br>
    <Col span="20" style="border-bottom: solid #EBEBEB;">
    </Col>
    <Col span="3"></Col>
  </Row>
<!--  排队界面-->
  <Row align="bottom">
    <Col span="1">
    </Col>
    <Col span="7">
      <br>
      <br>
      <p style="font-size: 16px;font-family: 'PingFang SC';margin-bottom: 10px" >组队逻辑
        <i-Switch size="large">
        <span slot="open">时间</span>
        <span slot="close">随机</span>
      </i-Switch>
      </p>
    </Col>
    <Col span="7">
      <br>
      <br>
      <p style="font-size: 16px;font-family: 'PingFang SC';margin-bottom: 5px">组内人数
        <Button @click="groupMemberNum--" shape="circle" style="margin-right: 10px"> - </Button>
        <label style="border-radius: 30%;border: solid #9D81FF;background-color: #9D81FF">  {{groupMemberNum}}  </label>
        <Button @click="groupMemberNum++" shape="circle" style="margin-left: 10px"> + </Button>
      </p>
    </Col>
  </Row>
  <Row style="margin: 30px">
    <Col span="24">
<!--      创建排队卡片，每个卡片传入一组人的名字-->
      <groupCard :groupStu="MemberName[index]" v-for="(item, index) in MemberName" :list-num="index" :key="item.index" ></groupCard>
    </Col>
  </Row>
</div>
</template>

<script>
import groupCard from '@/components/groupCard'
export default {
  name: 'courseDetail',
  props: {
    courseDetail: {
      type: Object,
      default: function () {
        return {
          courseName: '协同解难单元一',
          className: '班级A',
          inviteCode: 'AXSDS22'
        }
      }
    }
  },
  data () {
    return {
      groupMemberNum: 6
    }
  },
  components: {
    groupCard
  },
  methods: {
    // 以矩阵的方式获得所有进入课堂学生的名字集
    getMemberNameByGroup (groupmembernum) {
      return [
        ['张三', '李四', '王二', '麻子'],
        ['张三', '李四', '王二', '麻子'],
        ['张三', '李四', '王二', '麻子'],
        ['张三', '李四', '王二', '麻子']
      ]
    }
  },
  computed: {
    MemberName: function () {
      return this.getMemberNameByGroup()
    }
  }
}

</script>

<style scoped>
#courseDetail{
  text-align: left;
}
h1{
  font-family: "PingFang SC";
  color: #6B6B6B;
  font-size: 24px;
}
h2{
  font-family: "PingFang SC";
   color:#8A8A8A;
  font-size: 20px;
}

</style>
