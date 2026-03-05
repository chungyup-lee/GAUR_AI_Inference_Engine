<p align="center">
  <img src="assets/BISON_AI_Inference_banner.png" width="100%" alt="BISON AI Banner">
</p>


# 🐂 BISON AI Inference Engine

**BISON_AI Engine**은 다양한 컴퓨터 비전 모델을 최적의 성능으로 실행하기 위해 설계된 **고성능 크로스 플랫폼 C++ AI 추론 라이브러리**입니다. 

TensorRT, OpenVINO, ONNX Runtime 등 다중 백엔드를 단일 인터페이스로 통합하여, 하드웨어 환경(NVIDIA GPU, Intel CPU/GPU 등)에 맞춰 유연하게 모델을 배포하고 실시간 추론을 수행할 수 있습니다. 특히 산업용 비전 검사 장비(Windows DLL)와 엣지 디바이스(NVIDIA Jetson) 환경을 모두 완벽하게 지원합니다.

---

## 🚀 Key Features

### 1. Multi-Backend Architecture
단일 API를 통해 시스템 사양에 최적화된 엔진을 선택적으로 사용할 수 있습니다.
* **NVIDIA TensorRT:** v8.6 및 v10.0 선택 가능, 최강의 GPU 추론 속도 제공.
* **Intel OpenVINO:** 인텔 CPU 및 내장 GPU 자동 감지 및 최적화 가속.
* **ONNX Runtime:** CPU 및 CUDA Execution Provider를 통한 범용적 추론 지원.

### 2. Comprehensive Vision Tasks
산업 현장에서 요구되는 다양한 최신 AI 모델 구조를 내장하고 있습니다.
* **Classification:** EfficientNet 시리즈 지원.
* **Object Detection:** YOLOv5 (NMS, Bounding Box 후처리 내장).
* **Segmentation:** YOLOv5-Seg (마스크 추출 및 **Contour(윤곽선)** 변환 최적화).
* **Anomaly Detection:** PyramidFlow 기반의 이상치 탐지.

### 3. Cross-Platform & Hardware Ready
* **Windows (DLL):** `lib.cpp`를 통한 C# 및 Windows 응용 프로그램용 인터페이스 제공. (예외 처리 및 Crash Dump 기능 포함)
* **Jetson (Linux):** `lib_Jetson.cpp`를 통해 ARM64 기반 리눅스 환경 및 전력 효율 최적화.


---

## 📂 Architecture & Core Modules

```text
BISON_AI_Project/
├── AI.cpp / .h          # 모델별(YOLO, EfficientNet 등) 전/후처리 및 메모리 관리
├── Platform.cpp / .h    # 백엔드 엔진(TRT, ONNX, OpenVINO) Factory 패턴 및 I/O 관리
├── TrtLib.cpp           # TensorRT 엔진 로드 및 비동기 추론(H2D, D2H, Stream) 구현
├── OnnxLib.cpp          # ONNX Runtime 세션 관리 및 Tensor 할당
├── OpenvinoLib.cpp      # OpenVINO 모델 컴파일 및 추론 실행
├── lib.cpp              # [Windows] DLL Export 인터페이스 및 시스템 예외 처리 로직
├── lib_Jetson.cpp       # [Jetson] Shared Library 인터페이스 (ARM64 최적화)
└── utils.cpp            # Sigmoid, Contour 변환(masks2segments) 등 수학/영상처리 유틸
```

## 🛠 Tech Stack
| 분류 (Category) | 상세 기술 (Technology) |
| :--- | :--- |
| **Language** | C++ 20 (C-style Export API 지원) |
| **Computer Vision** | OpenCV 4.x |
| **Inference Backends** | TensorRT, OpenVINO, ONNX Runtime |
| **Acceleration** | CUDA, cuDNN, cuBLAS |
| **OS Support** | Windows 10/11, Ubuntu 20.04/22.04 (JetPack) |


## 🧑‍💻 Author
SangWook Park (박상욱) Senior Engineer @ BISON

📧 swpark@bison0507.com


## 🪪 License
본 프로젝트는 BISON의 자산이며, 무단 복제, 배포 및 사용은 엄격히 금지됩니다.

Copyright © BISON. All rights reserved.
