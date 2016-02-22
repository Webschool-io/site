# Webschool.io Site

## Átomos

- logo
- titulo-curso
- titulo-modulo
- titulo-aula
- video
- slides
- apostila

## Moléculas

- aula
  + titulo-aula
  + video
  + slides
  + apostila
- modulo
  + titulo-modulo
  + aulas

## Organismos

- cursos
  + titulo-curso
  + modulos

## Estilizando

Primeiramente devemos estilizar os átomos como sendo a base de tudo, para isso vamos definir regras bem simples para que sigam um padrão de cores e tamanhos e principalmente sua **responsividade**.

```css
.atom-logo {
  display: block;
  width: 20%;
  max-width: 30%;
  margin: 0 auto;
}
.atom-titulo-curso {
  color: #1437DE;
  font-size: 2.2rem;
}
.atom-titulo-modulo {
  color: #1437DE;
  font-size: 1.8rem;
}
.atom-titulo-aula {
  color: #1437DE;
  font-size: 1.4rem;
}
.atom-video {
  display: block;
  margin: 1em auto;
  width: 90%;
}
.atom-slides {
  color: #666;
  font-size: 1.8rem;
  font-weight: bold;
  text-decoration: underline;
}
.atom-apostila {
  color: #666;
  font-size: 1.8rem;
  font-weight: bold;
  text-decoration: underline;
}
```

Depois de definido os átomos vamos criar a estrutura do HTML pois dessa forma fica mais fácil visualizar os componentes do que apenas no CSS.

```html
<img class="atom-logo" src="./assets/images/logo-webschool.png" alt="Logo da Webschool.io" title="Logo da Webschool.io">

<main class="organism-cursos">
  <h1 class="atom-titulo-curso">Be MEAN</h1>
</main>
```

O código acima é o nível mais alto da nossa hierarquia, logo você deve se perguntar:

> Ué mas átomo no mesmo nível do organismo?

**Exatamente!** Porque no Atomic Design o átomo é a menor parte **independente** dos componentes, logo a `img` com o `atom-logo` pode estar em qualquer sozinho, porém para agrupar mais átomos precisamos criar uma molécula:


```html
<img class="atom-logo" src="./assets/images/logo-webschool.png" alt="Logo da Webschool.io" title="Logo da Webschool.io">

<main class="organism-cursos">
  <h1 class="atom-titulo-curso">Be MEAN</h1>

  <section class="molecule-modulos">
    <h2 class="atom-titulo-modulo">MongoDB</h2>
    
  </section>
</main>
```

Percebeu que os títulos, nesse layout, são todos átomos pois não os agrupamos com `hgroup`. 

Descendo mais um pouco na nossa química de estilos iremos criar uma reação entre 2 moléculas:


```html
<img class="atom-logo" src="./assets/images/logo-webschool.png" alt="Logo da Webschool.io" title="Logo da Webschool.io">

<main class="organism-cursos">
  <h1 class="atom-titulo-curso">Be MEAN</h1>

  <section class="molecule-modulos">
    <h2 class="atom-titulo-modulo">MongoDB</h2>
    
    <article class="molecule-aula">
      <h3 class="atom-titulo-aula">Aula 1</h3>
      
    </article>

  </section>
</main>
```

**Percebeu que colocamos 1 molécula dentro de outra?**

```html
<section class="molecule-modulos">
  <h2 class="atom-titulo-modulo">MongoDB</h2>
  
  <article class="molecule-aula">
    <h3 class="atom-titulo-aula">Aula 1</h3>

  </article>
</section>
```

Pense como sendo uma reação química de absorção.

> Absorção na química é um fenômeno ou processo físico ou químico em que átomos, moléculas ou íons introduzem-se em alguma outra fase, normalmente mais massiva, e fixam-se. O processo pode se dar pela fixação de um gás por um sólido ou um líquido, ou a fixação de um líquido por um sólido.
A substância absorvida se infiltra na substância que absorve, diferentemente da adsorção, já que espécies químicas submetidas a absorção são absorvidas pelo volume, não pela superfície (como no caso de adsorção). 

*fonte: [https://pt.wikipedia.org/wiki/Absor%C3%A7%C3%A3o_(qu%C3%ADmica)](https://pt.wikipedia.org/wiki/Absor%C3%A7%C3%A3o_(qu%C3%ADmica))*

Nesse caso a molécula absorvida foi `molecule-aula`, agora finalizamos com seus átomos internos já que essa é nossa menor molécula:


```html
<article class="molecule-aula">
  <h3 class="atom-titulo-aula">Aula 1</h3>
  
  <div class="atom-video">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/leYxsEAL_yY?list=PL77JVjKTJT2gXHb9FEokJsPEcoOmyF1pY" frameborder="0" allowfullscreen></iframe>
  </div>

  <div>
    <a class="atom-slides" href="https://docs.google.com/presentation/d/1_CHh_fTkzgxAnxB3MlZ5WRhTqMLViMk__jkCZiZ3IMA/edit?usp=sharing">Slides</a>
    <a class="atom-apostila" href="https://github.com/Webschool-io/be-mean-instagram">Apostila</a>
  </div>
</article>
```

Deixando nosso HTML assim:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="./assets/css/style.css">
  <title>Webschool.io</title>
</head>
<body>
  <img class="atom-logo" src="./assets/images/logo-webschool.png" alt="Logo da Webschool.io" title="Logo da Webschool.io">

  <main class="organism-cursos">
    <h1 class="atom-titulo-curso">Be MEAN</h1>

    <section class="molecule-modulos">
      <h2 class="atom-titulo-modulo">MongoDB</h2>
      
      <article class="molecule-aula">
        <h3 class="atom-titulo-aula">Aula 1</h3>
        
        <div class="atom-video">
          <iframe width="560" height="315" src="https://www.youtube.com/embed/leYxsEAL_yY?list=PL77JVjKTJT2gXHb9FEokJsPEcoOmyF1pY" frameborder="0" allowfullscreen></iframe>
        </div>

        <div>
          <a class="atom-slides" href="https://docs.google.com/presentation/d/1_CHh_fTkzgxAnxB3MlZ5WRhTqMLViMk__jkCZiZ3IMA/edit?usp=sharing">Slides</a>
          <a class="atom-apostila" href="https://github.com/Webschool-io/be-mean-instagram">Apostila</a>
        </div>
      </article>

    </section>
  </main>
</body>
</html>
```

![](http://i.imgur.com/annpoOy.png)

Após essas 3 etapas (Átomo, Molécula e Organismo) iremos definir o Template, essa é a etapa onde posicionamos nossos elementos.

Vamos iniciar centralizando o conteúdo principal, o logo já foi previamente centralizado no padrão do seu átomo.

```css
.organism-cursos {
  text-align: center;
  margin: 0 auto;
  width: 90%;
}
```

![](http://i.imgur.com/7NMPb0e.png)