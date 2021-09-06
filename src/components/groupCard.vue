<!--教师端主页右侧的排队情况-->
<template>
  <Row id="groupCard" justify="space-between" align="middle">
    <Col span="1" >
      <h1>{{listNum+1}}</h1>
    </Col>
    <Col v-for="(item) in groupStu" :key="item" span="2" >
      <Avatar icon="ios-person" size="large" />
      <br>
      <label>{{item}}</label>
    </Col>
  </Row>
</template>

<script>
export default {
  name: 'groupCard',
  props: {
    listNum: {
      type: Number,
      default: -1
    },
    groupStu: {
      type: Array,
      default: function () {
        return []
      }
    }
  },
  data () {
    return {
      listNUM: 1
    }
  }
}

</script>

<style scoped>
#groupCard{
  border: 2px solid #E7E7E7;
  border-radius: 12px;
  width: 100%;
  height: 100px;
  background-color: #F8F8F8 ;
  margin-top: 20px;
}
h1{
  color: #9D81FF;
  font-family:PingFang SC;
  font-size: 32px;
  padding-left: 40px;
}
</style>
