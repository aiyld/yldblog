---
title: "联系勾搭"
permalink: "/contact.html"
---

<form action="https://formspree.io/{{site.email}}" method="POST">    
<p class="mb-4">请在此发送消息，我会尽快回复!</p>
<div class="form-group row">
<div class="col-md-6">
<input class="form-control" type="text" name="name" placeholder="您的大名*" required>
</div>
<div class="col-md-6">
<input class="form-control" type="email" name="_replyto" placeholder="邮箱*" required>
</div>
</div>
<textarea rows="8" class="form-control mb-3" name="message" placeholder="消息*" required></textarea>    
<input class="btn btn-success" type="submit" value="发送">
</form>