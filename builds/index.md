---
layout: default
title: Build status dashboard

builds:
  - name: clipmenu
    disable:
      - lgtm
      - coveralls
  - name: srt
  - name: tzupdate
  - name: yturl
---

# Build status dashboard

<table>
  <thead>
    <tr>
      <th>Repository</th>
      <th>Tests</th>
      <th>Code quality</th>
      <th>Coverage</th>
      <th>Dependencies</th>
    </tr>
  </thead>
  <tbody>
    {% for repo in page.builds %}
    <tr>
      <th><a href="https://github.com/cdown/{{ repo.name }}">{{ repo.name }}</a></th>
      <td class="status-image">
        {% if repo.disable contains 'travis' %}
        N/A
        {% else %}
        <a href="https://travis-ci.org/cdown/{{ repo.name }}">
          <img class="nonstandard" src="https://img.shields.io/travis/cdown/{{ repo.name }}/develop.svg?label=are" alt="Linux build status for {{ repo.name }}" />
        </a>
        {% endif %}
      </td>
      <td class="status-image">
        {% if repo.disable contains 'lgtm' %}
        N/A
        {% else %}
        <a href="https://lgtm.com/projects/g/cdown/{{ repo.name }}/history/">
          <img class="nonstandard" src="https://img.shields.io/lgtm/grade/python/github/cdown/{{ repo.name }}.svg?label=is" alt="Code quality for {{ repo.name }}" />
        </a>
        {% endif %}
      </td>
      <td class="status-image">
        {% if repo.disable contains 'coveralls' %}
        N/A
        {% else %}
        <a href="https://coveralls.io/r/cdown/{{ repo.name }}">
          <img class="nonstandard" src="https://img.shields.io/coveralls/cdown/{{ repo.name }}/develop.svg?label=is" alt="Coverage for {{ repo.name }}" />
        </a>
        {% endif %}
      </td>
      <td class="status-image">
        {% if repo.disable contains 'requires' %}
        N/A
        {% else %}
        <a href="https://libraries.io/github/cdown/{{ repo.name}}">
          <img class="nonstandard" src="https://img.shields.io/librariesio/github/cdown/{{ repo.name }}.svg?label=are" alt="Dependency status for {{ repo.name }}" />
        </a>
        {% endif %}
      </td>
    </tr>
    {% endfor %}
  </tbody>
</table>

---

The [srt repo](https://github.com/cdown/srt) is where new changes to general
testing strategy go first.
