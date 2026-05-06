# flutter-face-recognition-auth

Autenticação biométrica em Flutter usando reconhecimento facial. Projeto de estudo e portfólio focado em demonstrar uso de visão computacional no dispositivo (on-device) com Google ML Kit, sem envio de imagens para servidores externos.

## Objetivo

Construir um fluxo completo de cadastro e login facial em um aplicativo Flutter:

- Captura de rosto via câmera frontal
- Detecção e extração de embeddings faciais
- Armazenamento local seguro do template biométrico
- Verificação 1:1 (login) comparando o rosto atual com o template salvo
- Liveness detection básico (piscar / virar a cabeça) para evitar foto estática

## Stack

- **Flutter** 3.x / Dart 3.x
- **google_mlkit_face_detection** — detecção de rosto on-device
- **camera** — captura de imagem em tempo real
- **tflite_flutter** — embeddings faciais via modelo TensorFlow Lite (FaceNet / MobileFaceNet)
- **flutter_secure_storage** — armazenamento criptografado dos embeddings
- **provider** ou **riverpod** — gerência de estado

## Arquitetura

```
lib/
├── core/                # config, theme, utils
├── data/
│   ├── repositories/    # face_repository, auth_repository
│   └── sources/         # secure_storage, camera_service
├── domain/
│   ├── entities/        # face_template, user
│   └── usecases/        # enroll_face, verify_face, liveness_check
└── presentation/
    ├── pages/           # enroll_page, login_page, home_page
    └── widgets/         # camera_preview, face_overlay
```

## Roadmap

- [ ] Configuração inicial do projeto Flutter e da camera
- [ ] Integração com ML Kit Face Detection
- [ ] Geração de embeddings com modelo TFLite
- [ ] Cadastro facial (enrollment) com múltiplas amostras
- [ ] Verificação facial e cálculo de similaridade (cosine distance)
- [ ] Liveness detection (eye blink / head turn)
- [ ] Telas de UI/UX polidas
- [ ] Testes unitários nas regras de comparação

## Como executar

```bash
flutter pub get
flutter run
```

> Requer permissão de câmera. Em iOS, configure `NSCameraUsageDescription` no `Info.plist`.

## Licença

MIT
