---
title: "请作者喝杯咖啡呀"
permalink: "/buy-me-a-coffee.html"
---

方式     | 地址
--- | -----
BTC:    | 17LB9ZCzvbGDZzYoUV2RPTX3E88y7pxthi
BCH:    | 17LB9ZCzvbGDZzYoUV2RPTX3E88y7pxthi
ETH:    | 0x2b3246b2f13e586839d9dcb173f5c6cffaf46930

<div class="container">
<h4 class="font-weight-bold spanborder"><span>{{page.title}}</span></h4>
    <div class="row gap-y listrecent listrecent listauthor">
    {% for reward in site.rewards %}
        <div class="col-lg-6 mb-4">
          <div class="p-4 border rounded">
            <div class="row">
              <div class="col-md-3 mb-4 mb-md-0">
                <img alt="{{reward.name}}" src="{{site.baseurl}}/{{ reward[1].logo }}" class="rounded-circle" height="80" width="80">
              </div>
              <div class="col-md-9">
                <div>
                  <h4 class="text-dark mb-0"> {{reward[1].name}} </h4>
                  <small class="d-inline-block mt-1 mb-3 font-weight-normal"></small>
                  <div class="excerpt">{{reward[1].addr}}</div>
                </div>
              </div>
            </div>
          </div>
        </div>
    {% endfor %}
    </div>
</div>
