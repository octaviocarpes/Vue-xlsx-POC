<template>
    <div class="import-xlsx">
        <div class="drag-n-drop-container">
            <p class="import-container-text">
                Drag file Here!
            </p>
        </div>
        <div class="import-button-container">
            <input type="file" name="" id="fileupload" @change="importFile">
        </div>
    </div>
</template>
<script>
import XLSX from 'xlsx'
import grid from 'canvas-datagrid'

export default {
    name: "import-xlsx",
    props:{
        sheet: Array
    },
    methods: {    
      importFile(e) {
            var rABS = true; 
            var files = e.target.files, f = files[0];
            var reader = new FileReader();
            var self = this;
            reader.onload = function(e) {
                var data = e.target.result;
                if(!rABS) data = new Uint8Array(data);
                var workbook = XLSX.read(data, {type: rABS ? 'binary' : 'array'});
            /* DO SOMETHING WITH workbook HERE */
            // Get sheets data (cells)
                const obj = workbook.Sheets['Sheet JS'];
                Object.keys(obj).forEach(function(key) {
                    const regex = /[a-zA-Z]{1}\d+/
                    if (regex.test(key)) {
                        console.log(self.sheet)
                        self.sheet.push(obj[key].v)
                    }
                });
                let grid = self.grid.canvasDatagrid()
                let size = self.sheet.size()
                for(i = 0; i < size; i++) {
                    
                }
            };
            if(rABS) reader.readAsBinaryString(f); else reader.readAsArrayBuffer(f);
        }
    }
};
</script>
<style lang="scss" scoped>
$lightBlue: #9cc4ed;

.import-xlsx {
    display: flex;
    flex-direction: column;
    justify-content: center;
}

.drag-n-drop-container {
  width: 150px;
  height: 150px;
  border: 5px dashed $lightBlue;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.import-button-container {
    width: 150px;
    padding: 5px;
}

.import-button {
    border: none;
    width: 150px;
    height: 50px;
    background-color: $lightBlue;
    font-size: 15px;
    font-weight: bold;
    color: white;
    border-radius: 25px;
    cursor: pointer;
}

.import-button:hover {
    opacity: .8;
    cursor: pointer;
}
</style>
