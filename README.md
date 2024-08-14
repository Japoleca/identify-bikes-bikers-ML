# Projeto de Classificação de Imagens usando YOLOv5: Pessoas com e sem Bicicletas
## Visão Geral
Este projeto tem como objetivo utilizar a arquitetura YOLOv5 para classificar imagens em duas categorias: __pessoas com bicicletas__ e __pessoas sem bicicletas__. O código foi desenvolvido e testado no Google Colab, utilizando a integração com o Google Drive para armazenar as imagens de entrada e os resultados processados. O projeto se concentra em detectar pessoas e bicicletas em imagens e classificar se uma pessoa está ou não montada em uma bicicleta, salvando as imagens processadas em diretórios separados.

## Estrutura do Projeto
### 1. Configuração do Ambiente
O projeto começa com a configuração do ambiente de desenvolvimento no Google Colab:

Montagem do Google Drive: O Google Drive é montado para acessar e salvar as imagens diretamente na nuvem.

Instalação de Dependências: As bibliotecas necessárias, incluindo uma versão específica do PyTorch e do OpenCV, são instaladas. O repositório YOLOv5 é clonado, e as dependências adicionais são instaladas a partir de um arquivo requirements.txt.

### 2. Carregamento do Modelo YOLOv5
O modelo YOLOv5s é carregado utilizando o repositório torch.hub. Este modelo pré-treinado é adequado para tarefas de detecção de objetos e é configurado para identificar objetos como "pessoas" e "bicicletas" nas imagens.

### 3. Funções de Suporte
Duas funções de suporte são definidas:<br>
- is_overlapping(box1, box2): Verifica se duas caixas delimitadoras (bounding boxes) estão sobrepostas, o que ajuda a determinar se uma pessoa está montada em uma bicicleta.

- draw_boxes(img, boxes, labels, colors): Desenha caixas delimitadoras nas imagens, com rótulos e cores, para visualização das detecções.

### 4. Processamento das Imagens
As imagens são processadas em um loop, onde cada imagem no diretório de entrada (input_folder) é lida e passada pelo modelo YOLOv5. O código realiza as seguintes etapas para cada imagem:

1. Detecção de Pessoas e Bicicletas: As detecções são filtradas para identificar apenas pessoas e bicicletas.

2. Verificação de Sobreposição: A função is_overlapping é usada para verificar se há uma pessoa sobre uma bicicleta.

3. Desenho das Caixas Delimitadoras: As caixas delimitadoras para as pessoas e bicicletas são desenhadas na imagem, com cores diferentes para cada categoria.

4. Classificação e Salvamento: Se uma pessoa estiver sobre uma bicicleta, a imagem é salva no diretório with_bike. Caso contrário, a imagem é salva no diretório without_bike.

### 5. Armazenamento dos Resultados
As imagens processadas são armazenadas em diretórios específicos:

- output_folder_with_bike: Imagens com pessoas montadas em bicicletas.

- output_folder_without_bike: Imagens de pessoas sem bicicletas.

### 6. Execução e Monitoramento
Durante a execução do código, uma mensagem de status é impressa para cada imagem processada, indicando onde ela foi salva.

## Considerações Finais
Este projeto demonstra uma aplicação prática do YOLOv5 em uma tarefa de detecção e classificação de objetos. A capacidade de distinguir entre pessoas com e sem bicicletas tem aplicações em monitoramento de segurança, análise de trânsito e estudos urbanos. O código pode ser facilmente adaptado para outras tarefas de detecção e classificação, dependendo dos objetos de interesse.

## Instruções para Execução
Configure o ambiente no Google Colab instalando as dependências e clonando o repositório YOLOv5.
Prepare as imagens de entrada no Google Drive, organizadas no diretório especificado no código.
Execute o código no Colab para processar as imagens, monitorando os resultados e ajustando os parâmetros, se necessário.
Revise as imagens processadas nos diretórios de saída para validar a precisão do modelo e a classificação realizada.
Aplicações Futuras
O código pode ser expandido para incluir outras categorias de objetos ou para ser treinado em um conjunto de dados personalizado, aumentando sua aplicabilidade em diferentes cenários.
