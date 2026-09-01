# Segmentação de Lesões de Esclerose Múltipla em Ressonância Magnética 3D

Pipeline completo de processamento de imagens médicas para segmentação automática de lesões hiperintensas de esclerose múltipla em exames de ressonância magnética (MRI) 3D (sequências T1 e FLAIR), desenvolvido como projeto da disciplina de Processamento Digital de Imagens 3D e Vídeos (PDIV3D) — UFSCar.

## Pipeline

1. **Redução de ruído** — comparação entre Filtro Bilateral, Difusão Anisotrópica e Média Não-Local (NLM); o Filtro Bilateral foi selecionado por preservar melhor as bordas relevantes
2. **Registro espacial** — alinhamento de atlas probabilístico (substância branca, cinzenta e líquor) ao espaço da imagem clínica, com avaliação de registro rígido, afim, BSpline e deformável (Model Zoo, grid 24)
3. **Segmentação** — comparação entre K-Means e Gaussian Mixture Model (GMM, 5 componentes) para identificação de lesões na substância branca

## Resultados

Comparação entre os métodos no caso de referência (voxel a voxel, contra máscara manual):

| Método | Dice | Jaccard | Precisão | Recall |
|---|---|---|---|---|
| K-Means | 0.6254 | 0.4550 | 0.6547 | 0.5986 |
| **GMM** | **0.6271** | **0.4568** | **0.7079** | 0.5629 |

O GMM superou o K-Means em Dice, Jaccard e Precisão, com trade-off de menor Recall — indicando resultado mais conservador (menos falsos positivos).

Aplicado aos demais casos clínicos com a mesma configuração de parâmetros, o método apresentou Dice entre 0.17 e 0.63, variando conforme as características de cada paciente.

## Tecnologias

Python — NumPy, Pandas, SciPy, scikit-learn (KMeans, GaussianMixture), SimpleITK, ITK, Matplotlib

## Sobre o projeto

Trabalho desenvolvido em dupla, com foco na comparação de métodos clássicos e não supervisionados aplicados a um problema real de imagem médica.

## Dados

Este notebook foi desenvolvido com acesso a um dataset institucional de imagens de ressonância magnética não incluído neste repositório, por questões de privacidade de dados médicos. Para reprodução, seria necessário adaptar os caminhos de leitura para uma base de dados equivalente.

## Como executar

Instale as dependências com:
\`\`\`
pip install -r requirements.txt
\`\`\`
