---
title: "请作者喝杯咖啡呀"
permalink: "/buy-me-a-coffee.html"
---

<div class="container">
<h4 class="font-weight-bold spanborder"><span>{{page.title}}</span></h4>
    <div class="row gap-y listrecent listrecent listauthor">
    {% for reward in site.rewards %}
        <div class="col-lg-6 mb-4">
          <div class="p-4 border rounded">
            <div class="row">
              <div class="col-md-2 mb-4 mb-md-0">
                <img alt="{{reward[1].name}}" src="{{site.baseurl}}/{{ reward[1].logo }}" class="rounded-circle" height="80" width="80">
              </div>
              <div class="col-md-10">
                <div>
                  <h4 class="text-dark mb-0"> {{reward[1].name}} </h4>
                  <div class="excerpt">{{reward[1].addr}}</div>
                </div>
              </div>
            </div>
          </div>
        </div>
    {% endfor %}
    </div>
</div>
