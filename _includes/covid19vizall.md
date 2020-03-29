{%- assign base_link = "https://github.com/taruma/inkovis/raw/master" -%}
{%- assign collection = site.data.covid19viz -%}


{%- for item in collection -%}

<figure class="figure w-100">
  <img src="{{ base_link }}/{{ item.folder_image}}/{{ item.image_filename}}.{{ item.image_format}}" class="figure-img img-fluid rounded" alt="{{ item.caption }} ({{ item.data}} {{ item.add_caption }})">
    <figcaption class="figure-caption text-center">{{ item.caption }} ({{ item.data}} {{ item.add_caption }})</figcaption>
</figure>

{%- endfor -%}

