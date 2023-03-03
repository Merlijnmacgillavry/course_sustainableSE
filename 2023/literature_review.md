---
title: Literature Review on Individual and Social Sustainability
---

{% for publication in site.literature_review_2023 reversed%}

{% assign currentdate = publication.year %}
{% if currentdate != date %}
### 📅 **{{ currentdate }}**
{% assign date = currentdate %} 
{% endif %}

  <p markdown="span">
      {{publication.author}} ({{publication.year}}).
      {%- unless publication.disable-page %}
      [**{{publication.paper_title}}**]({{publication.url | relative_url}}).
      {%- else %}
      **{{publication.paper_title}}**
      {%- endunless %}
      {%- if publication.journal %}
        *{{publication.journal}}*{% if publication.pages %} (pp. {{publication.pages}}){% endif %}.
      {% endif -%}
{%-for tag in publication.tags %}
<span class="badge">{{tag}}</span>
{% endfor %}
</p>
{%- if publication.annotation %}
<blockquote><small markdown="1">
{{publication.annotation | truncate: 300 }} [Read more.]({{publication.url | relative_url}})
</small></blockquote>
{% endif -%}

{% endfor %}

## How to contribute

To add a new paper, follow the instructions below:

1. Fork the repo of the website on Github: <https://github.com/luiscruz/course_sustainableSE/>
2. Create a new markdown file inside the directory `_literature_review_2023`
  - Use the following filename format: `<year>_<first_name_of_first_author>_<first_meaningful_word_of_title>.md`
  - Use the file `2021-author-keyword.md` has a template
  - If you want to add an image, add it to `2023/img/literature_review`
3. Commit, Push.
4. Submit a pull request.

Before submitting the pull request, you should test whether your file is rendering properly in the website. The easiest way to check it is by running the docker container, as instructed in the [Github Readme](https://github.com/luiscruz/course_sustainableSE).

Your page should be listed here: <http://localhost:4000/course_sustainableSE/2023/literature_review>

If you don't want to deal with Docker, you can do it the slow and expensive way: 1) enable *github pages* in your fork repo 2) check your the deployed page. (I don't recommend it, though)

*Note: let me know if you run into any issue or if there's any step you think should be explained here.*
