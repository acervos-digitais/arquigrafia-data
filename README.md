# arquigrafia-data

Dados sobre imagens do acervo [arquigrafia.org.br](https://www.arquigrafia.org.br/) gerados a partir de código em https://github.com/acervos-digitais/arquigrafia-utils.

## JSON

### `objects.json`:

Informação geral sobre imagens, no formato:

```json
{
  "images": {
    image_id: {
      "boxes": {
        object_label: [x0%, y0%, x1%, y1%],
        object_label: [x0%, y0%, x1%, y1%],
        ...,
      },
      "captions": {
        "en": {
          model_label: caption,
          model_label: caption,
          ...,
        },
        "pt": {
          model_label: caption,
          model_label: caption,
          ...,
        },
      },
      "dominant_color": {
        "by_count": [ R, G, B ],
        "by_hue": [ R, G, B ],
        "palette": [
          [ R0, G0, B0 ],
          [ R1, G1, B1 ],
          [ R2, G2, B2 ],
          [ R3, G3, B3 ],
        ],
      },
    },
    ...,
  },
  "objects": {
    object_label: [ image_id, image_id, image_id, ..., ],
    object_label: [ image_id, image_id, image_id, ..., ],
    ...,
  },
}
```

Onde:
- `image_id`: numero de id da imagem
- `object_label`: nome de objetos detectados
- `[x0%, y0%, x1%, y1%]`: local do objeto na imagem, relativo às dimensões da imagem
- `model_label`: nome do modelo usado para fazer a descrição (`blip`, `cpm`, `gpt` ou `vit`)
- `caption`: a descrição da imagem dada por um certo modelo
- `by_count`: cor mais frequente na imagem
- `by_hue`: cor frequente mais saturada na imagem
- `palette`: 4 cores mais frequentes na imagem

### `captions.json`:

Descrições das imagens, geradas a partir de 4 modelos distintos (`blip`, `cpm`, `gpt` ou `vit`), no formato:

```json
{
  image_id: {
    "en": {
      model_label: caption,
      model_label: caption,
      ...,
    },
    "pt": {
      model_label: caption,
      model_label: caption,
      ...,
    },
  },
  ...,
}
```

Onde:
- `image_id`: numero de id da imagem
- `model_label`: nome do modelo usado para fazer a descrição (`blip`, `cpm`, `gpt` ou `vit`)
- `caption`: a descrição da imagem dada por um certo modelo

### `captions_en.json` e `captions_pt.json`:

Descrições das imagens, geradas a partir do modelo `gpt` (`gpt-4o-2024-08-06`), no formato:

```json
{
  image_id: caption,
  image_id: caption,
  ...,
}
```

Onde:
- `caption`: a descrição da imagem dada por um certo modelo
