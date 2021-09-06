<template>
  <div>
  <div v-if="courseCardClicked==0" class="classCrad0">
    <Row>
      <Col span="20">
        <p style="text-align: left;font-size: 24px;line-height: 24px">{{ courseNameDetail.courseName }}</p>
      </Col>
      <Col span="4">
        <img src="../assets/more_icon@2x.png" style="width: 24px;height: 24px">
      </Col>
    </Row>
    <Row v-for="(item,index) in courseNameDetail.className" :key="item.index" >
      <!--      <Button v-if="index==0" @click="buttonClicked(index)" class="classLabel0" long style="margin: 5px">{{item}}</Button>-->
      <Button  @click="buttonClicked(index)" class="classLabel" long style="margin: 5px">{{item}}</Button>
    </Row>
  </div>
  <div v-else class="classCrad1">
    <Row>
      <Col span="20">
        <p style="text-align: left;font-size: 24px;line-height: 24px">{{ courseNameDetail.courseName }}</p>
      </Col>
      <Col span="4">
        <img src="../assets/more_icon@2x.png" style="width: 24px;height: 24px">
      </Col>
    </Row>
    <Row v-for="(item,index) in courseNameDetail.className" :key="item.index" >
<!--      <Button v-if="index==0" @click="buttonClicked(index)" class="classLabel0" long style="margin: 5px">{{item}}</Button>-->
      <Button  @click="buttonClicked(index)" class="classLabel" long style="margin: 5px">{{item}}</Button>
    </Row>
  </div>
  </div>
</template>

<script>
export default {
  name: 'courseCard',
  props: {
    courseNameDetail: {
      type: Object
    },
    courseCardClicked: {
      type: Number
    }
  },
  methods: {
    // 点击按钮后，这一个button变色
    // 获取父组件传递来的当前选项卡index,获取当前所有按钮，计算当前按钮下标，修改样式
    buttonClicked (index) {
      const btn = document.getElementsByClassName('classLabel')
      const submark = ((this.courseCardClicked) * (this.courseNameDetail.className.length) + index)
      for (let item of btn) {
        item.style.backgroundColor = '#FFFFFF'
        item.style.color = 'black'
      }
      btn[submark].style.color = 'white'
      btn[submark].style.backgroundColor = '#9D81FF'
    }
  }
}
</script>

<style scoped>
.classLabel{
  font-family: PingFangSC-Medium;
  font-size: 18px;
  color: #6B6B6B;
  text-align: left;
  line-height: 24px;
  font-weight: 500;
  width: 100%;
  border: #FFFFFF;
}
.classCrad0{
  background-color:#FFFFFF;
  padding: 20px;
  box-shadow: #6B6B6B;
  border: 2px solid #E7E7E7;
  border-top-left-radius: 12px;
  border-top-right-radius: 12px;
}
.classCrad1{
  background-color:#FFFFFF;
  padding: 20px;
  box-shadow: #6B6B6B;
  border: 2px solid #E7E7E7;
}
</style>
