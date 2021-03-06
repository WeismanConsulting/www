{# Set the `speakers` and `conf` variables before including this template #}

{% for talk in data %}

{% for speaker in talk.speakers %}
.. _speaker-{{ conf }}-{{ speaker.slug }}:
{% endfor %}

.. Comment to break up reference issues

.. raw:: html

                  {% for speaker in talk.speakers %}
                  <a name="speaker-{{ speaker.slug }}"></a>
                  {% endfor %}

                  <div class="well well--fluid-height">
                    {% for speaker in talk.speakers %}

                    <div class="speakers__person">
                      <figure>
                        <img class="speaker-image" src="/_static/img/speakers/{{ speaker.img_file }}" />
                        <figcaption>
                          <h5>{{ speaker.name }}</h5>
                        </figcaption>
                      </figure>

                      {% if speaker.twitter %}
                      <div class="speakers__socials">
                        <a href="https://twitter.com/{{ speaker.twitter }}">@{{ speaker.twitter }}</a>
                      </div>
                      {% endif %}
                    </div>
                    <div class="speakers__clear"></div>

                  {% endfor %}

                    <div class="speakers__clear"></div>
                    <div class="speakers__date">
                    </div>
                    <div class="speakers__content">
                      <h3>{{ talk.title }}</h3>
                      {% if talk.video%}
                      <p><strong><a href="{{ talk.video }}">Watch the video</a></strong>.</p>
                      {% endif%}
                      {% if talk.slides %}
                      <p><strong><a href="{{ talk.slides }}">View the slides</a></strong>.</p>
                      {% endif%}
                      {{ talk.abstract|indent(10) }}
                    </div>
                  </div>

{% endfor %}
