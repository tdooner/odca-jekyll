---
layout: default
---
{% assign candidate = page %}

<h1>{{ candidate.name }}</h1>
<div>
  <img style="width: 10rem; border-radius: 5rem;" src="{{ candidate.photo_url }}" alt="{{ candidate.name }}" />
</div>
<div><a href="{{ candidate.website_url }}">{{ candidate.website_url }}</a></div>
<div><a href="{{ candidate.twitter_url }}">{{ candidate.twitter_url }}</a></div>
<p>{{ candidate.content }}</p>

<p>Contributions: {{ candidate.total_contributions | money }}</p>
<p>Expenditures: {{ candidate.total_expenditures | money }}</p>
<p>Loans: {{ candidate.total_loans_received | money }}</p>
