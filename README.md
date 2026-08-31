# <img width="2432" height="1750" alt="rag_studio_logo" src="https://github.com/user-attachments/assets/4a77e8ee-b2df-43eb-aebf-04a776ed285c" /> RAG Studio

<p align="center">
  <img width="1120" height="1120" alt="logo_transparent" src="https://github.com/user-attachments/assets/dc1a22cc-8525-40e7-8c3d-a9b1496e496d" />
</p>

<p align="center">
  <strong>Plataforma Desktop Local de Inteligência Artificial e RAG Autónomo de Alto Desempenho</strong><br />
  Aceleração por GPU/NPU • Motor Dual-IA • Indexação Documental Privada • Explorador Hugging Face
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Versão-2.8.0-blue?style=flat-square" alt="Version 2.8.0" />
  <img src="https://img.shields.io/badge/Tauri-v2-orange?style=flat-square&logo=tauri" alt="Tauri v2" />
  <img src="https://img.shields.io/badge/FastAPI-8001-009688?style=flat-square&logo=fastapi" alt="FastAPI" />
  <img src="https://img.shields.io/badge/LLaMA-llama.cpp-yellow?style=flat-square" alt="llama.cpp" />
  <img src="https://img.shields.io/badge/Licença-MIT-green?style=flat-square" alt="License MIT" />
  <img src="https://img.shields.io/badge/Privacidade-100%25_Local-purple?style=flat-square" alt="100% Local" />
</p>

---

## 📖 Visão Geral

O **RAG Studio** é uma aplicação desktop concebida para executar modelos de linguagem avançados (LLMs) em formato **GGUF** diretamente no teu computador, garantindo **privacidade absoluta (zero envio de dados para a nuvem)** e tirando o máximo partido do teu hardware através de aceleração por GPU (CUDA / Vulkan) e NPU.

Integra um sistema completo de **RAG (Retrieval-Augmented Generation)** que permite conversar com documentos locais de forma contextualizada, assistido por um motor **Dual-IA** que otimiza as tuas perguntas antes da geração de resposta.

---

## ⚡ Principais Funcionalidades

* **🔒 100% Local & Privado:** Os modelos, históricos de conversação e documentos indexados ficam guardados exclusivamente no teu disco.
* **🚀 Motor LLaMA de Alto Rendimento:** Suporte a Flash Attention (`-fa on`), quantização de KV Cache (`q8_0`) para evitar saturação de VRAM e gestão automática de camadas GPU (`-ngl`).
* **📚 Sandbox Documental RAG:** Ingestão de ficheiros (`.pdf`, `.docx`, `.txt`, `.md`, `.csv`) numa pasta isolada `Documentos/` com divisão inteligente em blocos (*chunks*) e pesquisa vetorial sob demanda.
* **🧠 Motor Dual-IA (SLM na NPU/CPU):** Orquestração paralela onde um modelo leve (1B a 3B) refina a pergunta e extrai termos de pesquisa para a base RAG em milissegundos antes da GPU principal processar a resposta final.
* **🤗 Explorador Hugging Face Integrado:** Pesquisa, filtros de modelos GGUF, diagnóstico de compatibilidade de memória (VRAM/RAM), deteção de ficheiros já instalados e download assíncrono.
* **📊 Telemetria de Hardware em Tempo Real:** Velocímetro SVG com picos de velocidade de Raciocínio (🧠) e Resposta (⚡), monitorização de VRAM, RAM, CPU e temperatura.
* **💬 Isolamento de Conversas:** Separação estrita entre o **Chat Normal** e o **Chat RAG**, com histórico gravado em ficheiros `.json` na pasta `Conversas/`.
* **🌍 Suporte Multilingue (6 Idiomas):** Interface com internacionalização completa em Português (PT), English (EN), Français (FR), Español (ES), Deutsch (DE) e Italiano (IT).
* **🛑 Encerramento Limpo:** Termina todos os processos e servidores em segundo plano ao fechar a janela, sem bloquear ficheiros nem portas no sistema.

---

## 🖥️ Requisitos de Sistema

| Componente | Mínimo | Recomendado |
| :--- | :--- | :--- |
| **Sistema Operativo** | Windows 10 / 11 (64-bit) | Windows 11 (64-bit) |
| **Processador (CPU)** | Intel Core i5 / AMD Ryzen 5 (4 núcleos) | Intel Core i7 / AMD Ryzen 7+ |
| **Memória RAM** | 8 GB DDR4 | 16 GB DDR5 ou superior |
| **Placa Gráfica (GPU)** | 4 GB VRAM (compatível DirectX 12) | NVIDIA RTX (6 GB+ VRAM com suporte CUDA) |
| **NPU (Opcional)** | Não obrigatório (Fallback para CPU) | Intel AI Boost, AMD Ryzen AI, Snapdragon X |
| **Armazenamento** | 500 MB (Aplicação base) | 20 GB+ livres para modelos GGUF |

---

## 📥 Como Instalar e Executar

Podes descarregar os executáveis oficiais diretamente na secção de **[Releases](https://github.com/Miguel7258/RAG-Studio/releases)**:

### Opção 1: Versão Instalador (.exe)
1. Descarrega `RAG-Studio_2.8.0_x64-setup.exe`.
2. Executa o instalador e segue os passos simples do assistente.
3. Abre o programa pelo atalho no Ambiente de Trabalho ou Menu Iniciar.

### Opção 2: Versão Portátil (Zero-Install)
1. Descarrega `RAG_Studio_v2.8.0_Portable.zip`.
2. Extrai o conteúdo do ficheiro ZIP para uma pasta à tua escolha.
3. Executa o ficheiro `RAG_Studio.exe`.

---

## 📁 Estrutura de Pastas da Aplicação

```text
RAG_Studio/
├── RAG_Studio.exe          # Executável principal da aplicação (Tauri v2)
├── Conversas/              # Histórico das tuas conversas (.json)
├── Documentos/             # Ficheiros locais adicionados à base de conhecimento RAG
├── models/                 # Modelos GGUF descarregados
├── backend/                # Motor local de IA e endpoints FastAPI
└── assets/                 # Recursos visuais e logótipos

```

---

## 🛠️ Tecnologias e Arquitetura

* **Core Desktop:** [Tauri v2](https://tauri.app/) (Rust)
* **Frontend:** [React 18](https://react.dev/), [TypeScript](https://www.typescriptlang.org/), [Tailwind CSS](https://tailwindcss.com/), Lucide Icons, KaTeX
* **Backend:** [FastAPI](https://fastapi.tiangolo.com/), Uvicorn, Python 3.11
* **Motor de Inferência:** [llama.cpp](https://github.com/ggerganov/llama.cpp) (llama-server)
* **Pipeline RAG:** PyPDF, python-docx, SentenceTransformers

---

## 📄 Licença e Créditos

Distribuído sob a licença **MIT**. Consulta o ficheiro `LICENSE` para mais detalhes.

* **Autor:** Miguel
* **Desenvolvimento e Parceria Técnica:** Antigravity (Google Gemini)
* **Repositório:** [https://github.com/Miguel7258/RAG-Studio](https://github.com/Miguel7258/RAG-Studio)
