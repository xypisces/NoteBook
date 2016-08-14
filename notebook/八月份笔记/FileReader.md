<h3>HTML5-File</h3>
```javascript
    var fileInput = doucment.getElementById('test-image-file');
    var info = document.getElementById('test-file-info');
    var preview = document.getElementById('test-image-preview');
    //添加监听事件
    fileInput.addEventListener('change',function(){
        preview.style.background='';
        if(!fileInput.value){
            info.innerHTML = '没有选择文件';
            return;
        }

        var file = fileInput.files[0];
        info.innerHTML = '文件:'+file.name;
        if(file.type!=='image/jpeg'){
            alert('不是有效图片');
            return;
        }

        var reader = new FileReader();
        reader.onload = function(e){
            var data = e.target.result;
            preview.style.backgroundImage = 'url('+data+')';
        }
        reader.readAsDataURL(file);
        })