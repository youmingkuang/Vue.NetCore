<template>
  <div style="padding: 30px 100px;">
    <vol-box :model.sync="viewModel" :height="450" :width="600" title="点击表的弹出框">
      <div slot="content">弹出框组件</div>
      <!--  <div slot="footer">这里可以自己扩展box，也可不用写 -->
      <div slot="footer">
        <Button type="info" @click="viewModel=false">确认1</Button>
        <Button type="info" @click="viewModel=false">确认</Button>
      </div>
    </vol-box>

    <Divider>其他组件</Divider>
    <Alert show-icon>table+表单数据/测试完整示例/表单布局/其他组件，都是对iview、element-ui二次封装，只需要按现的方式进行配置json数据及实现方法即可使用</Alert>

    <div class="com">
      <div style="  margin-top:30px;">
        <h3>上传excel文件</h3>
        <UploadExcel @importExcelAfter="importAfter" :url="url"></UploadExcel>
      </div>
      <div class="com-item">
        <UploadImg :src="comSrc1" :width="300"></UploadImg>
        <UploadImg :src="comSrc" :width="300"></UploadImg>
        <div>
          <VolMenu :onSelect="onSelect" :onOpenChange="onOpenChange" :options="menu"></VolMenu>
        </div>
        <div>
          <Button type="info" ghost @click="viewModel=true">弹出框</Button>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import VolMenu from "@/components/basic/VolMenu.vue";
import VolBox from "@/components/basic/VolBox.vue";
import UploadExcel from "@/components/basic/UploadExcel.vue";
import UploadImg from "@/components/basic/UploadImg.vue";
export default {
  components: { VolMenu, VolBox, UploadExcel, UploadImg },
  methods: {},
  methods: {
    importAfter() {
      //上传完成后处理
    },
    onOpenChange(id) {
      this.$message.error("打开菜单" + id);
    },
    onSelect(id) {
      this.$message.error("菜单点击" + id);
    }
  },
  data() {
    return {
      viewModel: false,
      url: "", //上传的url
      template: {
        //下载模板的路径及模板的文件名，如果url为空，则不会显示下载模板
        url: "/api/App_TransactionAvgPrice/DownLoadTemplate",
        fileName: "测试模板下载"
      },
      comSrc1: "",
      comSrc:
        "https://imgs-1256993465.cos.ap-chengdu.myqcloud.com/h5pic/x2.jpg",
      menu: [
        { id: 9, parentId: 2, name: "用户管理", orderNo: 1111 },
        { id: 8, parentId: 14, name: "字典数据", orderNo: 1000 },
        { id: 16, parentId: 15, name: "首页轮播图片", orderNo: 200 },
        { id: 48, parentId: 0, name: "Table+单表数据", orderNo: 200 },
        { id: 55, parentId: 0, name: "Table+主从表单", orderNo: 180 },
        { id: 74, parentId: 0, name: "测试完整示例", orderNo: 177 },
        { id: 56, parentId: 0, name: "表单布局", orderNo: 175 },
        { id: 29, parentId: 0, name: "其他组件", orderNo: 173 },
        { id: 72, parentId: 0, name: "移动H5开发", orderNo: 165 },
        { id: 2, parentId: 0, name: "用户基础信息", orderNo: 160 },
        { id: 66, parentId: 0, name: "静态页面发布", orderNo: 152 },
        { id: 64, parentId: 0, name: "代码在线生成器", orderNo: 150 },
        { id: 1, parentId: 0, name: "系统设置", orderNo: 140 },
        { id: 5, parentId: 0, name: "日志管理", orderNo: 130 },
        { id: 18, parentId: 15, name: "成交均价", orderNo: 120 },
        { id: 40, parentId: 23, name: "提问记录", orderNo: 111 },
        { id: 23, parentId: 45, name: "问答信息", orderNo: 110 },
        { id: 25, parentId: 29, name: "其他组件", orderNo: 110 },
        { id: 26, parentId: 45, name: "静态页面", orderNo: 105 },
        { id: 27, parentId: 26, name: "静态页面1", orderNo: 105 },
        { id: 57, parentId: 56, name: "单列表单", orderNo: 100 },
        { id: 49, parentId: 48, name: "基础表单+编辑只读", orderNo: 100 },
        { id: 38, parentId: 15, name: "省市列表", orderNo: 100 },
        { id: 71, parentId: 2, name: "vue权限管理", orderNo: 100 },
        { id: 61, parentId: 0, name: "系统", orderNo: 100 },
        { id: 28, parentId: 45, name: "资讯", orderNo: 95 },
        { id: 30, parentId: 28, name: "价格走势", orderNo: 95 },
        { id: 31, parentId: 28, name: "牛评", orderNo: 95 },
        { id: 32, parentId: 28, name: "会议活动", orderNo: 95 },
        { id: 33, parentId: 28, name: "我要加入", orderNo: 95 },
        { id: 76, parentId: 26, name: "其他组件", orderNo: 95 },
        { id: 58, parentId: 56, name: "两列表单", orderNo: 90 },
        { id: 50, parentId: 48, name: "自动绑定下拉框", orderNo: 90 },
        { id: 3, parentId: 2, name: "角色管理", orderNo: 90 },
        { id: 4, parentId: 1, name: "配置管理", orderNo: 90 },
        { id: 59, parentId: 56, name: "多列表单", orderNo: 80 },
        { id: 51, parentId: 48, name: "新增编辑删除表单", orderNo: 80 },
        { id: 34, parentId: 45, name: "我的", orderNo: 80 },
        { id: 36, parentId: 34, name: "系统消息推送", orderNo: 80 },
        { id: 37, parentId: 34, name: "意见反馈", orderNo: 80 },
        { id: 24, parentId: 56, name: "后台加载table数据", orderNo: 75 },
        { id: 35, parentId: 56, name: "可编辑的table", orderNo: 73 },
        { id: 60, parentId: 56, name: "Table+表单", orderNo: 70 },
        { id: 68, parentId: 48, name: "审核、启用图片支持", orderNo: 70 },
        { id: 77, parentId: 56, name: "表单只读", orderNo: 60 },
        { id: 52, parentId: 48, name: "导入导出表单", orderNo: 60 },
        { id: 11, parentId: 0, name: "历史记录", orderNo: 60 },
        { id: 69, parentId: 48, name: "前端自定义扩展", orderNo: 50 },
        { id: 70, parentId: 48, name: "后台自定义扩展", orderNo: 40 },
        { id: 14, parentId: 1, name: "系统字典", orderNo: 11 },
        { id: 65, parentId: 64, name: "Vue+后台代码生成", orderNo: 1 },
        { id: 62, parentId: 61, name: "菜单设置", orderNo: 1 },
        { id: 63, parentId: 61, name: "下拉框绑定设置", orderNo: 1 },
        { id: 53, parentId: 55, name: "主从基础表单", orderNo: 1 },
        { id: 54, parentId: 55, name: "可新增修改主从表单", orderNo: 1 },
        { id: 44, parentId: 23, name: "提问回复记录", orderNo: 1 },
        { id: 46, parentId: 15, name: "产业联盟", orderNo: 1 },
        { id: 41, parentId: 11, name: "图片上传记录", orderNo: 1 },
        { id: 7, parentId: 2, name: "角色权限分配", orderNo: 1 },
        { id: 17, parentId: 2, name: "用户注册信息", orderNo: 1 },
        { id: 39, parentId: 2, name: "用户Token生成记录", orderNo: 1 },
        { id: 67, parentId: 66, name: "生成静态页面", orderNo: 0 },
        { id: 42, parentId: 34, name: "消息推送记录", orderNo: 0 },
        { id: 47, parentId: 15, name: "test2019", orderNo: 0 },
        { id: 10, parentId: 11, name: "短信验证码发送记录", orderNo: 0 },
        { id: 43, parentId: 11, name: "静态页访问记录", orderNo: 0 },
        { id: 6, parentId: 5, name: "系统日志", orderNo: 0 },
        { id: 12, parentId: 4, name: "生成配置", orderNo: 0 },
        { id: 13, parentId: 1, name: "菜单设置", orderNo: 0 },
        { id: 45, parentId: 0, name: "其他不用节点", orderNo: 0 },
        { id: 75, parentId: 74, name: "前后台主从扩展用例", orderNo: null },
        { id: 73, parentId: 72, name: "移动H5开发打包介绍", orderNo: null }
      ]
    };
  }
};
</script>
<style scoped>
.com-item {
  display: inline-block;
  width: 100%;
  margin-top:30px;
}
.com-item > div {
  margin-left: 30px;
  float: left;
}
</style>