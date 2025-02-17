# Apresentação do Lab04 - Componentes, Mensagens, Eventos e Barramento

Estrutura de pastas:

~~~
├── README.md  <- arquivo apresentando a tarefa
│
└── images     <- arquivos de imagens usadas no documento
~~~

# Aluno
* Filipe Seidi Ishida Veronezi (RA: EX150364)

## Tarefa 1 - Web Components e Tópicos

~~~html
<dcc-button
  label="Mundo Política"
  topic="noticia/mundo/politica"
  message="Afeganistão: cinco mitos que dificultam compreensão da crise atual"
>
</dcc-button>

<dcc-button
  label="Brasil Política"
  topic="noticia/brasil/politica"
  message="Ministro da Justiça presta depoimento à PF sobre inquérito"
>
</dcc-button>

<dcc-button
  label="Brasil Dinos"
  topic="noticia/brasil/dinos"
  message="Brasileiros encontram raro fóssil de dinossauro em operação policial e registram duas novas espécies"
>
</dcc-button>

<dcc-button
  label="Bahia Dinos"
  topic="noticia/bahia/dinos"
  message="Fóssil confiscado na Bahia é um dos mais completos de dinossauro brasileiro"
>
</dcc-button>

<dcc-lively-talk
  character="https://harena-lab.github.io/harena-docs/dccs/tutorial/images/doctor.png"
  speech="I heard about: "
  subscribe="noticia/+/politica:speech"
>
</dcc-lively-talk>

<dcc-lively-talk
  character="https://harena-lab.github.io/harena-docs/dccs/tutorial/images/nurse.png"
  speech="I heard about: "
  subscribe="noticia/brasil/#:speech"
>
</dcc-lively-talk>

<dcc-lively-talk speech="I heard about: " subscribe="noticia/#:speech">
</dcc-lively-talk>
~~~

![Composition Screenshot](images/task-1.png)



## Tarefa 2 - Web Components e RSS

~~~html
<dcc-rss
  source="https://www.wired.com/category/science/feed"
  subscribe="next/rss/science:next"
  topic="rss/science"
>
</dcc-rss>

<dcc-rss
  source="https://www.wired.com/category/design/feed"
  subscribe="next/rss/design:next"
  topic="rss/design"
>
</dcc-rss>

<dcc-aggregator topic="aggregate/science" quantity="4" subscribe="rss/science">
</dcc-aggregator>

<dcc-button label="Ciências Próxima" topic="next/rss/science"></dcc-button>

<dcc-button label="Design Próxima" topic="next/rss/design"></dcc-button>

<dcc-lively-talk
  character="https://harena-lab.github.io/harena-docs/dccs/tutorial/images/doctor.png"
  subscribe="aggregate/science:speech"
>
</dcc-lively-talk>

<dcc-lively-talk
  character="https://harena-lab.github.io/harena-docs/dccs/tutorial/images/nurse.png"
  subscribe="rss/science:speech"
>
</dcc-lively-talk>

<dcc-lively-talk subscribe="rss/design:speech"></dcc-lively-talk>
~~~

![Composition Screenshot](images/task-2.png)



## Tarefa 3 - Painéis de Mensagens com Timer

~~~html
<dcc-rss
  source="https://www.wired.com/category/science/feed"
  subscribe="next/rss/science:next"
  topic="rss/science"
>
</dcc-rss>

<dcc-rss
  source="https://www.wired.com/category/design/feed"
  subscribe="next/rss/design:next"
  topic="rss/design"
>
</dcc-rss>

<dcc-button label="Inicia" topic="timer/start"></dcc-button>

<dcc-aggregator topic="aggregate" quantity="3">
  <subscribe-dcc topic="rss/science"></subscribe-dcc>
  <subscribe-dcc topic="rss/design"></subscribe-dcc>
</dcc-aggregator>

<dcc-lively-talk
  character="https://harena-lab.github.io/harena-docs/dccs/tutorial/images/doctor.png"
  subscribe="+/science:speech"
>
</dcc-lively-talk>

<dcc-lively-talk
  character="https://harena-lab.github.io/harena-docs/dccs/tutorial/images/nurse.png"
  subscribe="+/design:speech"
>
</dcc-lively-talk>

<dcc-lively-talk subscribe="aggregate:speech"></dcc-lively-talk>

<dcc-timer
  cycles="10"
  interval="1000"
  topic="next/rss/science"
  subscribe="timer/start:start"
>
</dcc-timer>
<dcc-timer
  cycles="5"
  interval="2000"
  topic="next/rss/design"
  subscribe="timer/start:start"
>
</dcc-timer>
~~~

![Composition Screenshot](images/task-3.png)
