# 🚀 Projeto de Detecção de Objetos: Bicicletas e Motos

Este repositório contém o código e os pesos treinados para um modelo de Visão Computacional focado na detecção das classes **`bicicleta`** e **`moto`**.

O projeto foi executado no ambiente **Kaggle** e migrou de uma configuração inicial problemática (Darknet/YOLOv3) para a arquitetura moderna **YOLOv8** (PyTorch) para garantir o treinamento eficiente na GPU.

---

## 🎯 Objetivo do Projeto

Detectar e classificar instâncias de **bicicletas** e **motos** em imagens, utilizando a arquitetura YOLO (You Only Look Once).

---

## 🛠️ Tecnologias Utilizadas

| Componente | Tecnologia | Versão | Função |
| :--- | :--- | :--- | :--- |
| **Framework** | **Ultralytics** | 8.x | Treinamento, Validação e Inferência (YOLOv8) |
| **Modelo Base** | **YOLOv8n** (Nano) | - | Modelo de detecção rápido e eficiente |
| **Ambiente** | **Kaggle** | - | Execução e GPU (Tesla P100) |
| **Linguagem** | **Python** | 3.11 | Linguagem principal |

---

## ⚙️ Configuração do Ambiente e Desafios (Contexto)

O projeto iniciou com o Darknet (YOLOv3), mas encontrou falhas críticas de compatibilidade no ambiente Kaggle (erros de compilação C/CUDA e Makefile). A solução foi a migração para o **YOLOv8 (PyTorch)**, que utiliza bibliotecas Python estáveis e pré-instaladas, resolvendo os problemas e garantindo o uso da GPU.

---

## 📈 Resultados do Treinamento

O treinamento de **25 épocas** com o YOLOv8n foi concluído em 0.004 horas (aproximadamente 15 segundos) na GPU, resultando nas seguintes métricas:

| Métrica | Valor | Observação |
| :--- | :--- | :--- |
| **mAP50 (Geral)** | **0.744 (74.4%)** | Excelente performance em detecções não rigorosas. |
| **mAP50-95** | **0.593 (59.3%)** | Boa performance em IoU rigoroso. |

### Performance por Classe

| Classe | Precisão (P) | mAP50 |
| :--- | :--- | :--- |
| **moto** | 1.000 (100%) | 0.995 |
| **bicicleta** | 0.435 | 0.492 |

---

## 📦 Arquivos do Repositório

| Arquivo/Pasta | Conteúdo | Finalidade |
| :--- | :--- | :--- |
| **`best.pt`** | Arquivo de peso do modelo treinado (YOLOv8). | **Modelo Final** (Pronto para inferência). |
| **`resultados_yolov8.zip`** | Pasta train2/ (inclui logs, gráficos, e métricas em CSV). | **Métricas e Logs** (Comprova o treinamento). |
| **`inferencia_visual.zip`** | Imagens de validação com detecções desenhadas. | **Prova Visual** da performance do modelo. |

---

### 🚀 Como Usar o Modelo (Inferência)

Para rodar o modelo (`best.pt`) em novas imagens ou vídeos, use o comando de inferência da Ultralytics:

```bash
# Necessário ter o pacote ultralytics instalado (pip install ultralytics)
!yolo predict model=best.pt source='caminho/para/sua/imagem.jpg'
