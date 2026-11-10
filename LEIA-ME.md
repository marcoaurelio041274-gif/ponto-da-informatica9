# Site Ponto da Informática: como publicar na Vercel

Esta pasta já está pronta para a Vercel. Não precisa instalar nem compilar nada.

## Conteúdo da pasta
- `index.html`: o site inteiro.
- `img/`, `intro.mp4`, `poster.jpg`, `og.jpg`: fotos, vídeo e imagem de prévia do link.
- `favicon.ico`, `favicon.png`, `apple-touch-icon.png`: ícone da aba do navegador.
- `vercel.json`: configuração da Vercel (cabeçalhos de segurança e cache das imagens).
- `robots.txt`: libera os buscadores.

## Caminho mais simples: GitHub + Vercel
1. Crie uma conta gratuita em github.com e outra em vercel.com (dá para entrar na Vercel com a conta do GitHub).
2. No GitHub, crie um repositório novo (por exemplo `ponto-da-informatica`).
3. Clique em **Add file > Upload files** e arraste todo o conteúdo desta pasta, mantendo a pasta `img`. Clique em **Commit changes**.
4. Na Vercel, clique em **Add New > Project**, escolha o repositório e clique em **Deploy**. Deixe "Framework Preset" como **Other** e não preencha comando de build.
5. Em cerca de um minuto a Vercel mostra o endereço do site, no formato `nome.vercel.app`.

Para alterar o site depois, troque o arquivo no GitHub (por exemplo `index.html`). A Vercel publica a nova versão sozinha.

## Alternativa: pelo computador, sem GitHub
Com o Node.js instalado, abra o terminal dentro desta pasta e rode:
```
npm i -g vercel
vercel --prod
```

## Endereço próprio (por exemplo pontodainformatica.com.br)
1. Registre o domínio em registro.br.
2. Na Vercel, abra o projeto, vá em **Settings > Domains** e adicione o domínio.
3. A Vercel mostra os registros DNS que você precisa criar. Cadastre exatamente esses valores no painel do Registro.br (**DNS**). A propagação pode levar de alguns minutos a algumas horas.

## Depois que o domínio estiver no ar (3 ajustes no `index.html`)
1. Prévia do link no WhatsApp: troque `content="og.jpg"` por `content="https://SEU-DOMINIO/og.jpg"` na linha `og:image`. Sem o endereço completo, o WhatsApp não mostra a imagem.
2. Google: dentro do bloco `application/ld+json`, acrescente a linha `"url": "https://SEU-DOMINIO",` logo abaixo de `"name"`.
3. Cadastre o site no perfil do Google Meu Negócio da loja.

## Onde editar os dados da loja
No fim do `index.html`, no bloco `<script>`:
- `WHATSAPP` e `TELEFONE`: número do WhatsApp.
- `PROMO`: faixa de promoção no topo (mude `ativa` para `true` e escreva o texto).
- `AVALIACOES`: depoimentos de clientes. A seção só aparece quando houver pelo menos um.
- `FOTOS`: fotos das peças (por exemplo `"Bateria": "img/bateria-peca.jpg"`).

O formulário de orçamento não envia dados para servidor nenhum: ele monta a mensagem e o cliente a envia pelo WhatsApp.
