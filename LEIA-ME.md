# Operação Nuketown — app para Android TV

Este projeto cria um app para Android TV que abre o jogo hospedado em
**https://operacaonuketown.netlify.app** em tela cheia. O jogo continua no site:
quando você atualizar o site, o app já mostra a versão nova, sem gerar outro APK.

## Como gerar o APK (sem instalar nada no computador)

1. Crie um repositório no GitHub (pode ser privado) e envie **o conteúdo desta pasta** para ele.
2. No repositório, abra a aba **Actions** → **Compilar APK** → **Run workflow**.
3. Quando terminar (uns 3 a 6 minutos), abra a execução e baixe o arquivo **operacao-nuketown-tv-apk**.
   Dentro dele está o `app-debug.apk`.

> Alternativa: abra a pasta no **Android Studio** (ele baixa tudo sozinho) e use
> *Build → Build APK(s)*. Se ele pedir para criar o Gradle Wrapper, aceite.

## Como instalar na TV

1. Na TV: **Configurações → Dispositivo → Segurança → Fontes desconhecidas** (o caminho varia por marca).
2. Passe o `app-debug.apk` para a TV por um destes caminhos:
   - **adb** (TV e computador na mesma rede): `adb connect IP_DA_TV` e `adb install -r app-debug.apk`
   - pendrive + app gerenciador de arquivos na TV
   - app **Downloader** na TV, abrindo um link direto para o arquivo
3. O app **Operação Nuketown** aparece na tela inicial da TV, com o banner do jogo.

## Controles na TV

- **Controle remoto:** setas e OK navegam pelos menus. **Voltar** fecha as opções, abre/fecha a pausa
  durante a partida e, no menu principal, sai do app.
- **Para jogar, use um gamepad** (Bluetooth ou USB). Aperte qualquer botão uma vez para ativá-lo.
  **Start** abre a pausa. O mouse não é usado na TV.
- O jogo precisa de **internet** (ele é carregado do site). Sem conexão, o app mostra uma tela com
  o botão "Tentar novamente".

## Vídeo e áudio da sala

A TV normalmente não tem câmera. Na janela de vídeo, o jogo mostra um **QR Code**: escaneie com o
celular para usar a câmera dele. O microfone depende do hardware da TV; o Android pergunta a permissão.

## Mudar o endereço do jogo

Edite as constantes `URL` e `HOST` no início de
`app/src/main/java/app/nuketown/tv/MainActivity.java`.

## Observações

- O APK gerado é de **depuração** (assinado com a chave de teste do Android). Serve para instalar
  na sua TV. Para publicar na **Google Play** é preciso um APK/AAB de *release* assinado com sua
  própria chave (e uma conta de desenvolvedor).
- O app usa o **WebView** do sistema. TVs muito antigas, com WebView desatualizado, podem rodar o
  jogo com baixo desempenho.
