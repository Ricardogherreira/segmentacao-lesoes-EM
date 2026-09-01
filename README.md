# Segmentação de Lesões de Esclerose Múltipla em Ressonância Magnética 3D

Pipeline completo de processamento de imagens médicas para segmentação automática de lesões hiperintensas em exames de ressonância magnética (MRI) 3D, desenvolvido como projeto da disciplina de Processamento de Imagens Digitais 3D (UFSCar).

## Pipeline

1. **Redução de ruído** — Filtro Bilateral, escolhido por preservar bordas relevantes durante a suavização das imagens
2. **Registro espacial** — Registro baseado em atlas (Model Zoo, grid 24), alinhando os volumes ao espaço padrão
3. **Segmentação** — Comparação entre K-Means e Gaussian Mixture Model (GMM) com 5 componentes, ambos métodos não supervisionados

## Resultados

O GMM superou o K-Means nas métricas avaliadas:
- **Dice**
- **Jaccard**
- **Precisão**

## Tecnologias

Python, NumPy, e bibliotecas de processamento de imagem médica (ver `requirements.txt` para lista completa de dependências)

## Sobre o projeto

Trabalho desenvolvido em dupla, com foco na comparação de métodos não supervisionados aplicados a um problema real de imagem médica.

## Dados

Este notebook foi desenvolvido com acesso a um dataset institucional de imagens de ressonância magnética não incluído neste repositório, por questões de privacidade de dados médicos. Para reprodução, seria necessário adaptar os caminhos de leitura para uma base de dados equivalente.

## Como executar

Instale as dependências com:
\`\`\`
pip install -r requirements.txt
\`\`\`
