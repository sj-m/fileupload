<body>
<!--multiple 区别-->
<input id="file" type="file" multiple/>
<button id="upload" type="button">upload</button>
</body>
<script type="text/javascript">
    $('#upload').bind('click', function () {
        <!--多文件-->
        var formData = new FormData();
        var files = $('#file')[0].files;
        for (var i = 0; i < files.length; i++) {
            formData.append('files', files[i]);
        }
        <!--单文件-->
        var formData = new FormData();
        var file = $('#file')[0].files[0];
        formData.append('file', file);
        $.ajax({
            url: '/oss/upload.json',
            type: 'POST',
            cache: false,
            data: formData,
            processData: false,
            contentType: false,
        }).done(function (res) {
            alert(res.success)
        }).fail(function (res) {
        });
    })
</script>

后台单文件通过MultipartFile接受文件信息，多文件MultipartFile[]
