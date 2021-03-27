# Foreground e Background no Android
Durante meus estudos sobre o Framework do Android, deparei-me com algumas dúvidas e confusões causadas pela sobrecarga de expressões e termos usados na documentação.

Este artigo é parte de minhas notas de estudo e me ajudaram bastante a entender melhor a filosofia e estrutura por trás desse framework.

Estas notas independem de linguagem de programação e meu foco é sobre arquitetura e conceitos gerais, sendo assim, aplicam-se em qualquer tecnologia de implementação que se faça uso.

 ## Filosofia Mestre do Android
O sistema Android foi criado com a prioridade ao usuário e sua experiência com a interface dos dispositivos! Por isso da expressão: "Make me Amazing!", que no português ficaria "Faça-me Extraordinário!". Enfim, experiência do usuário em primeiro lugar!

Lembrem-se disso! Afinal, tudo gira em torno do teu usuário, pois ele quem decide se fica ou sai do teu aplicativo...

## Foreground e Background
Toda a funcionalidade que tende a atender a interação com o usuário e compor a interface do usuário, incluindo: funcionalidades de navegação, apresentação, animação. É dito estar em foreground.
Essas funcionalidades apenas se atém a manter a atenção do usuário e conversar com ele.

Em contrapartida, todas as funcionalidades que dão significado ao teu aplicatido e que ocorrem nos bastidoses, como:  gravar informações nos dispositivos de armazenamento, processar dados e acessar a rede. Estes são ditos estarem em background.

Resumindo, tudo o que está interagindo com o usuário diz-se estar em foreground e tudo o que está escondido dele está em background.

### Tá bom, Mas e daí?
A importância desse conceito é vista ao olharmos melhor para os conceitos de componentes básicos do Android, onde ocorre uma divisão bem nítida disso.

Onde temos, como componente de foreground a Activity e de background o Service, Broadcast Receiver e o Content Provider.(A primeira vista esses termos parecem "bichos de sete cabeças", mas não se assute, conversaremos sobre eles em um momento futuro e com calma. Acredite, extenderiamos muito esse artigo...)

Os componentes de foreground sempre apresentarão algo ao usuário enquanto os outros serão executados, sem nem ao menos o usuário saber que eles existem. Essa é a mágica que criamos!

Em suma, o foreground conversa com o usuário enquanto o background suporta essa conversa!

### A Idéia Geral da Execução em Background
Tendo falado isso tudo, não seria de se espantar que tenhamos a Activity como um dos pontos de entrada primários de nossas aplicações. Mas atente que: Independente da linguagem de programação, nosso aplicativo inicia com uma linha de execução apenas e cabe a nós separar isso conforme a necessidade. Não é de se admirar que qualquer método seja executado junto e sequencialmente. Assim acontece com nosso aplicativo.

Se iniciamos um componente que roda ou executa em background, apenas o desvinculamos do ciclo de vida da Activity, mas não geramos uma linha de execução separada.

Desvincular uma execução do ciclo de vida da Activity é importante, pois esse é um dos componentes mais dinâmicos que temos, eles são recriados a qualquer modificação de posição de tela ou navegação. Imagine interromper uma tarefa importante e que dure mais tempo que a paciência de nosso usuário? - Isso não é incomum...
