A randomly ordered list of anvi'o developers and contributors.

<div class="anvio-people">
{% assign n = site.data.people | size %}
{% assign people = site.data.people | sample: n %}
{% for person in people %}
    {% include _person_text.html with_bio="True" %}
{% endfor %}
</div>