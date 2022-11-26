# Desafio:
> O objetivo deste trabalho, é simular os padrões de aterrissagem e decolagem em um aeroporto.<br>
Suponha um aeroporto que possui 3 pistas, numeradas como 1, 2 e 3.<br>
Cada pista possui sua respectiva fila de espera que recebe, por unidade de tempo, de 0 a 3 aeronaves. Essas aeronaves são identificadas com um ID (números sucessivos, de acordo com a ordem de chegada). Cada aeronave possui uma quantidade inicial de reserva de combustível, estipulada de forma randômica variando de 2 a 20.<br>
De acordo com a disponibilidade das pistas 1, 2 e 3, uma quantidade de aviões (0 a 3) é encaminhada para as pistas.<br>
Todas as pistas podem ser utilizadas para decolagem e pousos em geral. Porém, em casos emergenciais, a fila 3 pode ser reorganizada para que os aviões com menos combustível ganhem prioridade e pousem antes dos demais.<br>
Considere que no momento em que o avião toca a pista no seu pouso, a perda de unidades de combustível deixa de acontecer, pois tal consumo só será realizado durante o intervalo de tempo em que o avião permanece no ar (decolou mas ainda não pousou).<br>
Caso o avião possua apenas 1 unidade de combustível e na próxima rodada não haja pistas disponíveis para pouso (incluso a 3, pois o caso é emergencial), o avião cai.<br>
Se apenas uma aeronave está com falta de combustível, ela pousará na pista 3; se mais de um avião estiver nesta situação, as outras pistas poderão ser utilizadas (a cada unidade de tempo no máximo 3 aviões poderão estar nesta desagradável situação, caso contrário, os aviões excedentes irão cair).<br>
Utilize 6 caracteres (sendo 3 números e 3 letras) para gerar os ID dos aviões chegando nas filas de decolagem (aterrissagem). A cada unidade de tempo, assuma que os aviões entram nas filas antes que aterrissagem ou decolagem ocorram.<br>
Em cada rodada, devem ser impressos:<br>
a) o status de cada fila de espera (quantos aviões, seus IDs);<br>
b) o tempo médio de espera para decolagem (quantas rodadas serão necessárias para decolar);<br>
c) o tempo médio de espera para aterrissagem (quantas rodadas serão necessárias até que o avião possa pousar);<br>
d) o número de aviões que aterrissam sem reserva de combustível (quantidade de pousos emergenciais).<br>
Os itens b e c acima devem ser calculados para os aviões que já decolaram ou pousaram, respectivamente. A saída do programa deve ser auto-explicativa e fácil de entender.<br>
A entrada dos dados deve ser feita a partir de um gerador de números aleatórios.

# Solução
- **Projeto II - Sistema de gerenciamento de Voos:**

  

  ![Diagrama_Aeroporto_Fundo_Branco2.png](https://s2.loli.net/2022/10/27/4ciBsmD89PTZKoA.png)

  

- Nesse projeto, a equipe desenvolveu um sistema de gerenciamento de voos que funciona com as seguintes condições: 
  
  - O sistema inicia com o usuário digitando um valor do tipo inteiro, que será utilizado como unidade de tempo, cada vez que esse número é decrementado no sistema, entende-se que uma rodada passou.
  
  _____
  
  - Existem três pistas no aeroporto, conforme mostra a imagem, a Pista 2 é a única que serve para decolagem e aterrissagem, sendo que as aterrissagens que ocorrem nessa pista são preferencialmente em casos de emergência. Outra condição associada a pista 2 é que, mesmo ela sendo de decolagem e aterrissagem, em uma rodada de tempo ela só pode fazer uma operação por vez. A quantidade máxima de aviões permitida é 3 por pista, exceto na pista 2, que pode ter até 6 aviões, sendo 3 na fila de decolagem e 3 na fila de aterrissagem. 
  
  _____
  
  - Cada avião tem uma condição para ser gerado, os IDs possuem no mínimo 6 caracteres, sendo 3 números seguidos por 3 letras, o combustível dos aviões é definido por um random de número inteiro que pode variar de 2 até 20. O tempo de espera para decolagem e aterrissagem, são compostos por um número inteiro que vai sendo incrementado a cada rodada que o avião permanece na fila de decolagem ou aterrissagem (a fila que o avião aparece vai depender de uma função dentro do programa que é responsável por mover os aviões para as filas, respeitando o limite de quantidade). 
  
  _____
  
  - Aterrissagem de emergência: Existem uma função no programa chamada mover em emergência, que vai priorizar os aviões que estiverem com menor quantidade de combustível naquela rodada para realizar a aterrissagem, pois caso o combustível do avião seja zero, será exibida a informação em tela de que o avião caiu, juntamente com o seu respectivo ID. 
  
  _____
  
  - Aterrissagem: Os aviões que estiverem com maior quantidade de combustível, irão realizar a aterrissagem nas pista 1 ou 3. A ordem de aterrisagem dos aviões que não estão com pouco combustível ocorre por ordem de chegada, em um sistema de fila.
  
  _____
  
  - Decolagem: Só ocorre quando a pista 2 está livre, ou seja, quando não possui nenhum avião para aterrissar. 
  
  ____
  
  - A cada execução o usuário recebera na tela a seguinte informação: 
    - O número da rodada que o sistema está processando seguido pelos IDs dos aviões que estão se movimentando na rodada, a operação que estão realizando (decolagem ou aterrissagem) e a pista em que cada avião está realizando a operação.  
    - Abaixo dessa informação é exibido o estado de cada pista (que pode ser livre ou ocupada, esse estado, serve para impedir que a pista 2 realize mais de uma operação por rodada); 
    - A posição, o ID e o combustível de cada avião, nas filas das pistas, seguido pela quantidade de pousos emergenciais na pista. Por fim, é exibido o tempo médio de decolagem e por último o de aterrissagem, sendo a média de todas as pistas desde a primeira rodada até a rodada atual. 
  
  _____
  
  - No encerramento do programa, é gerado um arquivo CSV, com o nome "Dados aeroporto", que contém: 
    - Total de queda de aviões; 
    - Quantidade de pousos emergenciais; 
    - Tempo médio de espera para decolagem, seguido pelo de aterrissagem; 
    - Total de rodadas executadas.
  
  ____
  
  - Simulações realizadas: 
  
    - **Simulação 1:**
      - **Total de rodadas:** 4500;
      - **Percentual de queda:** cerca de 8%
      - **Pousos de emergência:** cerca de 3%
      - **Tempo médio de espera para decolagem:** Aproximadamente 8 rodadas; 
      - **Tempo médio de espera para aterrissagem:** Aproximadamente 2 rodadas; 
  
    ____
  
    - **Simulação 2:**
      - **Total de rodadas:** 6000;
      - **Percentual de queda:** cerca de 7%
      - **Pousos de emergência:** cerca de 5%
      - **Tempo médio de espera para decolagem:** Aproximadamente 8 rodadas; 
      - **Tempo médio de espera para aterrissagem:** Aproximadamente 2 rodadas; 

  - **Diagrama do Programa**<br>
      ![Diagrama_logica_2](https://user-images.githubusercontent.com/94374033/204093342-819d784f-7f27-4d35-a26d-1dbde2b7f9a3.png)
____

#### :busts_in_silhouette: Participantes:   

- [Joelson Silva](https://br.linkedin.com/in/joelsons)
- [Jhaidan Ribeiro](https://br.linkedin.com/in/jhaidan42)
- [Gustavo Henrique Siqueira](www.linkedin.com/in/gustavo-henriques)  
____



