<template>
  <div id="container" >
  <Row  style="background-color: #FFFFFF;box-shadow: 0 0 2px 0">
    <Col span="10"></Col>
    <Col span="2">
      <img src="../assets/logo@2x.png" style="width: 100%;height: 100%" alt="">
    </Col>
    <Col span="13"></Col>
  </Row>
  <br>
  <Row >
    <Col span="1"></Col>
    <!--      底部左侧选项-->
    <Col span="5" style="border-radius: 20px;">
<!--      // getCourse获得一个二维的矩阵，每一个item代表一个协同单元包含哪些班级-->
        <Row v-for="(item, index) in getCourses" :currentCardClicked="index" :key="item.courseName" >
          <Col span="24">
            <courseCard :courseNameDetail="item" :courseCardClicked="index"></courseCard>
          </Col>
        </Row>
    </Col>
    <Col span="1">
    </Col>
<!--    底部右侧解难单元课程详情-->
    <Col span="16">
      <courseDetail>
      </courseDetail>
    </Col>
  </Row>
  <br>
  </div>
</template>
<script>
import courseCard from '@/components/courseCard'
import courseDetail from '@/components/courseDetail'
export default {
  data () {
    return {
      // courses数据，传给coursecard
      getCourses: [
        {
          courseName: '协同解难单元一',
          className: ['班级A', '班级B']
        },
        {
          courseName: '协同解难单元二',
          className: ['班级A', '班级B']
        },
        {
          courseName: '协同解难单元三',
          className: ['班级A', '班级B']
        },
        {
          courseName: '协同解难单元四',
          className: ['班级A', '班级B']
        }
      ],
      currentCardClicked: -1
    }
  },
  components: {
    courseCard,
    courseDetail
  },
  methods: {
    courseCardClicked (event, index) {
      console.log(event)
      console.log(index)
      // console.log(((this.currentCardClicked + 1) * (index + 1) - 1))
      // const btn = document.getElementsByTagName('Button')[((this.currentCardClicked + 1) * (index + 1) - 1)]
      // btn.style.color = 'white'
      // btn.style.backgroundColor = '#9D81FF'
    }
  }
}
</script>
<style>
Row{
  background-color: #42b983;
}
#container{
  width: 100%;
  height:100%;
  background-color: #EEEEEE;
}
</style>
