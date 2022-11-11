---
category: ML
date: 2022-11-10
tags:
- FastAI
- Arcadia University
title: Is this a cute dog
fileName: cute_dog
categories: ML
lastMod: 2022-11-10
---
# My first image classifier
{{ < rawhtml >}}
<h2>An inline HTML block</h2>
<input id="photo" type="file">
<div id="results"></div>
<script>
  async function loaded(reader) {
    const response = await fetch('https://hf.space/embed/jph00/pets/+/api/predict/', {
      method: "POST", body: JSON.stringify({ "data": [reader.result] }),
      headers: { "Content-Type": "application/json" }
    });
    const json = await response.json();
    const label = json['data'][0]['confidences'][0]['label'];
    results.innerHTML = `<br/><img src="${reader.result}" width="300"> <p>${label}</p>`
  }
  function read() {
    const reader = new FileReader();
    reader.addEventListener('load', () => loaded(reader))
    reader.readAsDataURL(photo.files[0]);
  }
  photo.addEventListener('input', read);
</script>

{{ < /rawhtml >}}
