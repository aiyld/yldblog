---
title: "Buy me a coffee"
permalink: "/buy-me-a-coffee.html"
---

<div class="container">
    <div class="row gap-y listrecent listrecent listauthor">
    {% for reward in site.rewards %}
        <div class="col-lg-6 mb-4">
          <div class="p-4 border rounded">
            <div class="row">
              <div class="col-md-2 mb-4 mb-md-0">
                <img alt="{{reward[1].name}}" src="{{site.baseurl}}/{{ reward[1].logo }}" height="40" width="40">
              </div>
              <div class="col-md-7">
                <div>
                  <h4 class="text-dark mb-0"> {{reward[1].name}} </h4>
                  <div class="excerpt" style="word-break: break-all;">{{reward[1].addr}}</div>
                </div>
              </div>
              <div class="col-md-3" style="text-align: right;">
                <img alt="{{reward[1].name}} QR" src="{{site.baseurl}}/{{ reward[1].qr }}" height="86" width="86">
              </div>
            </div>
          </div>
        </div>
    {% endfor %}
    </div>
</div>
