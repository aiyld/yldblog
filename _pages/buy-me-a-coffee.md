---
title: "Buy me a coffee"
permalink: "/buy-me-a-coffee.html"
---

<div class="row buycoffee flexshow flex-wrap">
{% for reward in site.rewards %}
  <div class="coffee-outter flexshow">
    <div class="coffee-box flexshow align-items">
      <div class="coffee-addr flex">
        <h4 class="for-name flexshow">
          <img class="coffee-logo" alt="{{reward[1].name}}" src="/{{ reward[1].logo }}" height="40" width="40">
          <span style="line-height: 40px;">{{reward[1].name}}</span>
        </h4>
        <div class="excerpt" style="word-break: break-all;">{{reward[1].addr}}</div>
      </div>
      <div class="coffee-qr">
        <img alt="{{reward[1].name}} QR" src="/{{ reward[1].qr }}" height="86" width="86">
      </div>
    </div>
  </div>
{% endfor %}
</div>
