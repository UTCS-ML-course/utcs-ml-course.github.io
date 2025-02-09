---
title: "Lectures"
nav_order: 1
---

# Lectures

<!-- Lecture recordings are uploaded to [Panopto](https://mit.hosted.panopto.com/Panopto/Pages/Sessions/List.aspx#folderID=%22b2079bc7-0ca3-4fdf-a3e5-b1d4014c37ee%22). -->
<br>
<iframe width="560" height="315" src="https://www.youtube.com/embed/videoseries?si=Xg6yrukZ6ewrFRAg&amp;list=PL3rKtVun8xDW9ut_RA-OHev_Jxc4jdJc4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

{% assign limit_value = 24 %}  <!-- Set this to the number of lectures to display-->
{% assign sorted_lectures = site.lectures | sort: 'id' %}
{% assign filtered_lectures = sorted_lectures | slice: 0, limit_value %}

{% for lecture in filtered_lectures %}
## {{ lecture.title }}
- {% if lecture.topic %} **Topic:** {{ lecture.topic }} {% else %} {% endif %}
- {% if lecture.notes %} **[Notes / Slides]({{ lecture.notes }})** {% else %} **Notes:** *To be released* {% endif %}
<!-- - {% if lecture.slides %} **[Slides]({{ lecture.slides }})** {% else %} **Slides:** *To be released* {% endif %} -->
- {% if lecture.recording %} **[Recording]({{ lecture.recording }})** {% else %} **Recording** *To be released* {% endif %}
{% if lecture.additional_links %} - **Additional Links:** {% for link in lecture.additional_links %} 
    - [{{ link.name }}]({{ link.link }}) {% endfor %} {% endif %}
{% endfor %}


<!-- - {% if lecture.recording %} **[Recording]({{ lecture.recording }})** {% else %} **Recording:** *To be released* {% endif %} -->