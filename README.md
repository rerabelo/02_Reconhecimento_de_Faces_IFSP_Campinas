# Reconhecimento de Faces IFSP Campinas
Renata Rabelo e Mariana Cabride

O código depositado nesse repositório realiza várias etapas relacionadas ao treinamento e teste de redes neurais para reconhecimento facial utilizando o dataset PubFig83 disponibilizado no desafio do Kaggle elaborado para a disciplina de Aplicações em Ciência de Dados (D3APL 2023) do curso Especialização em Ciência de Dados do IFSP Campinas. Além disso, esse repositório é continuação da primeira tentativa desenvolvida para resolver o desafio que pode ser acessado no link: https://github.com/rerabelo/01_Reconhecimento_de_Faces_IFSP_Campinas


**Descrição das redes neurais adotadas:**
Foram adotadas três abordagens de redes neurais. A primeira foi uma Rede Neural Convolucional (CNN) personalizada, que contém duas camadas convolucionais, cada uma seguida por uma camada de max pooling, e duas camadas densas, sendo a última a camada de saída. Essa é uma arquitetura bastante comum para problemas de classificação de imagens.
Na segunda abordagem, aplicamos a técnica de Transfer Learning à CNN personalizada, mantendo as camadas convolucionais congeladas e substituindo a última camada densa por uma nova, de acordo com o número de categorias do conjunto de dados.
Por fim, adotamos a ResNet50 pré-treinada, uma das arquiteturas de rede neural convolucional mais populares e eficazes, também utilizando a técnica de Transfer Learning. A ResNet50 contém 50 camadas e foi treinada no conjunto de dados ImageNet, sendo, portanto, capaz de extrair características complexas das imagens.


**Pré-processamento:**
A etapa de pré-processamento envolve a leitura das imagens do conjunto de dados e a aplicação de transformações para deixá-las em um formato adequado para o treinamento da rede neural. Isso inclui redimensionar as imagens para as dimensões desejadas, converter a representação de cores de BGR para RGB e normalizar os valores dos pixels..


**Treinamento:**
Os modelos foram treinados utilizando o otimizador SGD e a função de perda 'sparse_categorical_crossentropy', adequada para tarefas de classificação multiclasse. Utilizou-se callbacks para parada antecipada (early stopping), a fim de interromper o treinamento se a perda de validação não melhorasse após um determinado número de épocas, e o TensorBoard, para visualizar as métricas de treinamento e validação.


**Otimizadores adotados:**
Foi utilizado o otimizador Stochastic Gradient Descent (SGD) com uma taxa de aprendizado de 0.01. SGD é uma versão estocástica do método de otimização de descida de gradiente, que atualiza os pesos do modelo de maneira iterativa com base nos dados de treinamento para minimizar a função de perda.


**Fine-tuning:**
No caso da ResNet50, além do Transfer Learning, também foi aplicado o fine-tuning, descongelando algumas das últimas camadas convolucionais do modelo base e permitindo que seus pesos fossem atualizados durante o treinamento. Isso permite que o modelo se ajuste mais ao conjunto de dados específico.


**Validação e discussão dos resultados:**
Os modelos foram validados usando o conjunto de validação e as métricas de perda e acurácia foram traçadas para cada época de treinamento. Em geral, a adoção de arquiteturas pré-treinadas como a ResNet50, junto com o Transfer Learning e o fine-tuning, tende a levar a melhores resultados em termos de acurácia devido à sua capacidade de extrair características complexas e ao fato de que já foram treinadas em grandes conjuntos de dados. No entanto, os resultados específicos dependem do conjunto de dados e da tarefa de classificação específica, e seria importante realizar uma análise mais detalhada dos resultados e talvez experimentar com diferentes arquiteturas, parâmetros de treinamento e técnicas de pré-processamento para obter desempenhos ainda melhores.

