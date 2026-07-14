# Galeria_flutter
# 📸 Desafio Nativo - Galeria de Fotos em Flutter

Este projeto foi desenvolvido como parte da **Atividade Prática: Recursos Nativos em Flutter**, ministrada na disciplina de Programação para Dispositivos Móveis. O trabalho é focado no **Tema 2: Galeria (Acesso ao Armazenamento de Mídia)**.

O objetivo deste aplicativo é demonstrar, de forma prática e visual, como interagir com os recursos nativos do sistema operacional (Android e iOS) para solicitar permissões de acesso à galeria, listar as mídias existentes, permitir a seleção e utilizar esses arquivos dentro da interface do usuário.

---

## 👤 Integrante
* **Maria de Fátima de Araújo Sousa** - 

## 🚀 Funcionalidades Demonstradas (Foco da Atividade)

O aplicativo cumpre rigorosamente os pontos focais exigidos na atividade prática:

1.  **Solicitação de Permissão:** O app gerencia a solicitação de permissão nativa para acessar o armazenamento de mídia no momento exato da intenção de uso.
2.  **Listagem e Seleção:** Utiliza o pacote `image_picker` para abrir a galeria nativa do sistema, permitindo listar e selecionar múltiplos arquivos de imagem simultaneamente.
3.  **Utilização no App:** As imagens selecionadas são recuperadas como arquivos (`XFile`) e renderizadas dinamicamente em uma grade interativa (`GridView`) na interface do Flutter.

---

## ⭐ Diferenciais de Implementação

Além dos requisitos básicos, implementei funcionalidades extras para melhorar a experiência do usuário (UX) e a qualidade do código:

* **Visualização Expandida (Zoom Nativo):** Ao tocar em qualquer imagem da grade, ela se abre em tela cheia (Modal Dialog) permitindo o gesto de pinça (`InteractiveViewer`) para zoom, simulando o comportamento de uma galeria profissional.
* **Remoção de Itens:** Adicionei um botão de lixeira sobre cada miniatura, permitindo gerenciar e remover fotos da lista temporária de forma simples.
* **Código Multiplataforma Inteligente:** O código detecta automaticamente se está rodando na Web (como no FlutLab.io) ou em um dispositivo móvel (`kIsWeb`), utilizando o método correto de carregamento de imagem (`Image.network` ou `Image.file`) para evitar erros de renderização.

---

## 🛠️ Configurações Nativas Realizadas (Permissões)

Para que o aplicativo funcione corretamente em dispositivos físicos (fora do ambiente web), foram realizadas as seguintes configurações nos arquivos nativos do projeto:

### 🤖 Android (`android/app/src/main/AndroidManifest.xml`)
Adicionadas as permissões de leitura de imagens na memória do dispositivo, garantindo compatibilidade com versões anteriores e posteriores ao Android 13 (API 33):
```xml
<uses-permission android:name="android.permission.READ_MEDIA_IMAGES" />
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" android:maxSdkVersion="32" />

<key>NSPhotoLibraryUsageDescription</key>
<string>Precisamos de acesso à sua galeria para você selecionar e visualizar fotos dentro do aplicativo.</string>
