# Python-Morfologia-M3
As operações morfológicas são técnicas de processamento de imagens que buscam modificar a forma e estrutura dos objetos que estão contidos na imagem. Criado na ferramenta Google Colab, este código na linguagem Python utiliza a biblioteca da OpenCV para realizar essas operações de processamento.

Primeiramente importamos as bibliotecas que são necessárias para a morfologia: "cv2" que é a da OpenCV; "numpy" que irá nos auxiliar com a manipulação de matrizes. Além disso, como foi utilizado o Colab, usamos o módulo "cv2_imshow" do pacote "google.colab.patches" para possibilitar a exibição de imagens neste ambiente Google.

São utilizadas três imagens a serem morfolizadas: "j.png", "j_ruido.png" e "j_furos.png". Estas imagens estão contidas no próprio documento do Colab.
Estas três imagens são carregadas em escala de cinza usando a função cv2.imread, e são atribuidas às variáveis img, img_opening, img_closing, respectivamente.

Em seguida é criada uma matriz 5x5 chamada "kernel" (, que está totalmente preenchida somente com o número 1 (np.ones((5,5),np.uint8). A importância desta matriz é porquê é ela quem define o tamanho da forma que será utilizada para as operações morfológicas de imagens.

Adiante, são realizados as operações morfológicas de erosão e dilatação na imagem "j.png". É utilizado o "cv2.erode" para erosão e "cv2.dilate" para dilatação. Além disso, devido ao "iterations = 2", cada operação é realizada duas vezes. Após isso, o resultado das erosões e dilatações são atribuidas às variáveis "erosion" e "dilation", respectivamente. Ambas as operações usam o Kernel como ferramenta. Na erosão, o tamanho dos objetos na imagem são diminuídos, enquanto na dilatação os objetos da imagem são aumentados. Após estas operações serem realizadas, é aplicado a operação de gradiente na imagem "j.png" utilizando o "cv2.morphologyEx" junto com o parâmetro "cv2.MORPH_GRADIENT", também com o uso do Kernel. Esta operação de gradiente é a diferença entre a dilatação e a erosão da imagem, o qual destaca as bordas da imagem "j.png".

Terminado as operações morfológicas na imagem "j.png", o código realiza a operação de abertura na imagem "j_ruido.png" e de fechamento na imagem "j_furos.png". Ambas as operações utilizam da função "cv2.morphologyEx" e do Kernel, mas a de abertura utiliza o parâmetro "cv2.MORPH_OPEN" e o fechamento "cv2.MORPH_CLOSE", e são atribuidos às variáveis "opening" e "closing", respectivamente. A operação de abertura remove os pequenos objetos e rúidos presentes na imagem, e o fechamento preenche os buracos presentes nos objetos.

E então, ao final do código é exibido as imagens em suas formas originais e em suas formas morfolizadas.
