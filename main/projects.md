---
title: "Final Project"
nav_order: 3
---

# Final Project

## Final Project Presentation & Report Guidelines

### Presentation

Final project presentations will take place on **April 23** and **April 28**. Each group should sign up for a presentation slot using the signup sheet linked below:

**[Sign-up Sheet](https://docs.google.com/spreadsheets/d/1zP819IPfeckT04ak12eiGkCK2Qtxs-c5nQYuHeXlq2I/edit?usp=sharing)**

Each presentation will be **15 minutes total**, consisting of:
- **10–12 minutes** for the presentation
- **3–5 minutes** for Q&A and discussion

We recognize that the final project report is due after the presentations, on **May 3**, so it is expected that you may not have all your results finalized by the time you present. In your presentation, you should cover:
- The problem you are addressing
- Some relevant background or motivation
- Your proposed methodology
- Intermediate results or progress so far
- Your plans for the remaining work before the report deadline

This is a good opportunity to receive feedback on your approach and in-progress results.

### Final Report

The final report is due on **May 3**. It should be a **5–10 page mini-paper** written in the format of a NeurIPS conference paper.

Please use the following LaTeX template to prepare your report:

**[NeurIPS 2024 Overleaf Template](https://www.overleaf.com/latex/templates/neurips-2024/tpsbbrdqcmsh)**

The report should:
- contain a link to your project code (either a github codebase or link to some cloud stored project folder) 
- clearly explain the motivation, approach, results, and insights from your project.

If you have any questions, feel free to contact the course staff.
<!-- Submit projects to [canvas](https://canvas.utexas.edu). -->

{% assign limit_value = 2 %}  <!-- Set this to the number of projects to display-->
{% assign sorted_projects = site.projects | sort: 'due_date' %}
{% assign filtered_projects = sorted_projects | slice: 0, limit_value %}

<!-- Debugging output -->
<!-- <p>Limit Value: {{ limit_value }}</p>
<p>Total Items: {{ total_items }}</p>
<p>Start Index: {{ start_index }}</p> -->
<!-- <p>Sorted projects:</p>
<pre>{{ sorted_projects | inspect }}</pre> -->
<!-- <p>Filtered projects:</p>
<pre>{{ filtered_projects |inspect }}</pre> -->

{% for proj in filtered_projects %}
## {{ proj.title }}

<!-- - **Release Date:** {{ proj.release_date | date: "%B %d, %Y" }} -->
- **Due Date:** {{ proj.due_date | date: "%B %d, %Y" }}
- {% if proj.pdf %} **[PDF]({{ proj.pdf }})** {% else %} **PDF:** *To be released* {% endif %}
{% if proj.description %} - {{proj.description}} {% endif %}
{% if proj.additional_links %} - **Additional Links:** {% for link in proj.additional_links %} 
    - [{{ link.name }}]({{ link.link }}) {% endfor %} {% endif %}

{% endfor %}

<!-- - {% if proj.gradescope_link %} **[Submit to Gradescope]({{ proj.gradescope_link }})** {% else %} **Submit to Gradescope:** *To be released* {% endif %} -->