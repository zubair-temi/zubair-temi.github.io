---
layout: default
title: ویڈیوز
permalink: /videos/
---

<h1 style="text-align:center; padding-top: 30px; padding-bottom:30px;">ویڈیوسیریز</h1>

<div class="row videos">
    
    {% for pl in site.data.video_playlists %}
        <div class="col-md-4 book">
            
            <div style="font-size:2rem;"><span><strong>{{ pl.name }}</strong></span></div>
            <a href="/videos/{{pl.url}}">
                <img src="//img.youtube.com/vi/{{pl.videos[0].id}}/0.jpg" width="220px"
                style="box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);">
            </a>
        </div>
    {% endfor %}

</div>