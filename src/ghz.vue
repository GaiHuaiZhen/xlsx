<template>
    <div>
     

 <input type="file" v-on:change="sendfile($event.target)" />
        <div id="zzdemo"></div>
<div v-on:click="hh">
    前端导出xlsx
</div>
    </div>
</template>
<script>
import XLSX from 'xlsx'

export default {
    data() {
        return {
             tableData: '', 
            tableHeader: '' 
        }
    },
     methods: {
//下载～～～～～～～～～～～～～～～～～～～～～～～～～～～～～～～～·
hh(){
    alert()
    var aoa = [
    ['姓名', '性别', '年龄', '注册时间'],
    ['张三', '男', 18, new Date()],
    ['李四', '女', 22, new Date()]
];
var worksheet = XLSX.utils.aoa_to_sheet(aoa);
var new_workbook = XLSX.utils.book_new();
 XLSX.utils.book_append_sheet(new_workbook, worksheet, "sheetjs");
     XLSX.writeFile(new_workbook, "D://sheetjs_json.xlsx");



},
//显示文件～～～～～～～～～～～～～～～～～～～～～～～～～～～～
     sendfile(obj) {
                 var zzexcel;
                console.log(obj)
                
                if(!obj.files) {
                    
                    return;
                }
                var f = obj.files[0];
                var reader = new FileReader();
                reader.readAsBinaryString(f);
                reader.onload = function(e) {
                    var data = e.target.result;
                        zzexcel = XLSX.read(data, {
                            type: 'binary'
                        });
                    for(var i=0;i<zzexcel.SheetNames.length;i++){
            　　　　　　document.getElementById("zzdemo").innerHTML +=zzexcel.SheetNames[i]+"="+JSON.stringify(XLSX.utils.sheet_to_json(zzexcel.Sheets[zzexcel.SheetNames[i]]))+"<br/>";
        　　　　　　}
                }
            }

    },
    mounted() {
//   this.$refs.upload.$el.querySelector('.el-upload__input').addEventListener('change', e => {
//     this.readExcel(e);
    
//   })
// var reader = new FileReader();
//         reader.onload = function (e) {
//           // 数据预处理
//           var binary = "";
//           var bytes = new Uint8Array(e.target.result);
//           var length = bytes.byteLength;
//           for (var i = 0; i < length; i++) {
//             binary += String.fromCharCode(bytes[i]);
//           }

//           /* 读取 workbook */
//           var wb = XLSX.read(binary, {
//             type: 'binary'
//           });

//           /* 选择第一个sheet */
//           var wsname = wb.SheetNames[0];
//           var ws = wb.Sheets[wsname];

//           /* excel转换json数组,加上{header:1}是普通数组，不写是对象数组 */
//           self.data = XLSX.utils.sheet_to_json(ws);
//           console.log(self.data);}






        







}
}
</script>