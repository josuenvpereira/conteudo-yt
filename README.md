# conteudo-yt — repositório PÚBLICO de conteúdo do squad-yt

Repositório **público** que hospeda os **outputs renderizados** (vídeos long-form, shorts verticais, thumbnails) da pipeline **squad-yt** (privada) e, no futuro, vai **rodar os renders** aqui.

> ⚠️ **A pipeline, o código e os segredos vivem no repo PRIVADO `squad-yt`.** Aqui ficam só os **artefatos públicos** (mídia pronta) e os workflows de render. **Nenhum segredo/chave neste repo** — ele é público.

## Por que um repo público separado

| Benefício | Motivo |
|---|---|
| **CI ilimitado** | GitHub Actions é **grátis e ilimitado** em repos **públicos** (no privado há teto de minutos). Os renders Remotion (pesados) passam a rodar aqui **sem custo**. |
| **URLs públicas** | A mídia ganha **URL pública direta** — necessária pra **hospedar o vídeo que o Instagram baixa** (a Graph API de Reels exige URL pública), e útil pra TikTok / YouTube Shorts / distribuição em geral. |
| **Repo de código limpo** | Mídia pesada (MP4) fica **fora** do repo da pipeline. |

## Estrutura

```
channels/
  <canal>/                 # ex: saiba
    videos/                # long-form master (16:9)
    shorts/                # shorts verticais (9:16) — 1 por conceito
    thumbnails/            # thumbnails (PNG)
.github/
  workflows/               # (futuro) render.yml / shorts.yml — CI ilimitado
```

**Convenção de nomes** (igual ao squad-yt): `canal` e `episodio_id` casam `[a-z0-9-]`.
Ex: `channels/saiba/shorts/01-4-jeitos-de-turbinar-ia/short-j1.mp4`

## Como a mídia vira URL pública (pro IG e distribuição)

- **Arquivo no tree** → `https://raw.githubusercontent.com/josuenvpereira/conteudo-yt/main/<caminho>`
  (bom pra arquivos pequenos — shorts ~10–20 MB).
- **GitHub Releases** → `https://github.com/josuenvpereira/conteudo-yt/releases/download/<tag>/<arquivo>`
  (melhor pra arquivos grandes — long-form ~100 MB — sem inchar o tree; serve via CDN, suporta ranges).
- **GitHub Pages** (opcional) → serve com `Content-Type` de vídeo correto (ideal pro IG, se necessário).

## Roadmap

- [x] Estrutura + convenções de pastas
- [ ] Hospedar os shorts aqui → vira o host do `instagram_publish.js` (substitui o litterbox, que é instável)
- [ ] Mover os workflows de render (`render.yml`, `shorts.yml`) do `squad-yt` pra cá → **CI ilimitado**
- [ ] (opcional) Ligar GitHub Pages pra `Content-Type` de vídeo

---
🤖 Estrutura criada pela pipeline **squad-yt** — companheiro público do repo privado.
