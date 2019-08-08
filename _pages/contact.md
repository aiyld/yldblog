---
title: "联系勾搭"
permalink: "/contact.html"
---

<div id="subssuccess" class="alert alert-primary alert-dismissible fade show" role="alert" style="display: none">
  <span>发行成功！</span>
  <button type="button" class="close" data-dismiss="alert" aria-label="Close">
    <span aria-hidden="true">&times;</span>
  </button>
</div>

<script>
  function submitMessageForm() {
    var form = document.getElementById('messageForm'),
    formData = new FormData(form);
    $.ajax({
      url:"https://www.samyoc.com/yoc/message?action=add",
      type:"post",
      data:formData,
      processData:false,
      contentType:false,
      done: function (res) {
      },
      success:function(res){
        $("#subssuccess").show();
      },
      error:function(err){
      }
    });

    return false;
  }
</script>

<form id="messageForm" method="POST" onsubmit="return submitMessageForm();">    
<p class="mb-4">请在此发送消息，我会尽快回复!</p>
<div class="form-group row">
<div class="col-md-6">
<input class="form-control" type="text" name="name" placeholder="您的大名*" required>
</div>
<div class="col-md-6">
<input class="form-control" type="email" name="email" placeholder="邮箱*" required>
</div>
</div>
<textarea rows="8" class="form-control mb-3" name="content" placeholder="消息*" required></textarea>    
<input class="btn btn-success" type="submit" value="发送">
</form>