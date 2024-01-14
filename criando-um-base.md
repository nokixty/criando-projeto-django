# CRIANDO UM BASE.HTML
Agora vamos criar nosso **base.html**, já aproveitando para importar o BootStrap. O base.html será usado como base para as demais páginas HTML, servindo, por exemplo, para programar um menu de navegação que aparecerá em todas as páginas. 

Após criar esse menu uma única vez no arquivo base, podemos importá-lo facilmente nas outras páginas, reutilizando o código e mantendo o nosso projeto mais simples e mais facilmente editável. O BootStrap, por sua vez, irá nos ajudar principalmente com a interface da nossa aplicação web.

Primeiro, vamos acessar o site do [BootStrap](https://getbootstrap.com/docs/5.3/getting-started/introduction/) para pegar os links necessários para a importação.

Você também pode [baixar](https://getbootstrap.com/docs/5.3/getting-started/download/) os arquivos do BootStrap e colocá-los na pasta static. 


Vamos criar na pasta template um arquivo **base.html**.

```html
{%load static%}

<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Base</title>

    <link rel="stylesheet" href="{% static 'css/styles.css' %}">
    <link rel="stylesheet" href="{% static 'css/bootstrap.min.css' %}">
</head>
<body>

    <script src="{% static 'js/bootstrap.bundle.min.js' %}"></script>
</body>
</html>
```

Com a página base criada e o BootStrap importado, nós podemos criar um layout inicial e utilizar mais um comando do Django para separar o nosso modelo em blocos:

Por exemplo:
```html
{% block nome_do_bloco %}
	conteúdo do bloco
{% endblock %}
```
Então, podemos importar o base para outras páginas e usar o mesmo **comando block** do Django para editar nossos arquivos html. 

### base.html
```html
{%load static%}

<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
<!-- BLOCO DO TITULO -->
    {%block title%} <title>Base</title> {%endblock%}
    
    <link rel="stylesheet" href="{% static 'css/styles.css' %}">
    <link rel="stylesheet" href="{% static 'css/bootstrap.min.css' %}">
    
</head>
<body>
<!-- BLOCO DA NAVBAR -->
    {%block navbar%}
        <nav class="navbar navbar-expand-lg bg-primary" data-bs-theme="dark">
            <div class="container-fluid">
            <span class="navbar-brand mb-0 h1">PROJETO DJANGO</span>
            </div>
        </nav>
    {%endblock%}

<!-- BLOCO DO CONTEUDO -->
    {%block content%}
        <h1> BASE DO MEU PROJETO </h1>
    {%endblock%}

<!-- BLOCO DO FOOTER -->
    {%block footer%}
        <div class="container-fluid bg-primary fixed-bottom" data-bs-theme="dark">
            <footer class="py-3 my-4">
            <ul class="nav justify-content-center pb-3 mb-3">
                <li class="nav-item"><a href="#" class="nav-link px-2 text-body-secondary">Sobre</a></li>
            </ul>
            <p class="text-center text-body-secondary">© 2024 Nokixty, Inc</p>
            </footer>
        </div>
    {%endblock%}

    <script src="{% static 'js/bootstrap.bundle.min.js' %}"></script>
</body>
</html>
```

Agora podemos substiuir o conteúdo do nosso **index.html**.

### index.html
```html
{%extends 'base.html'%}

{%block title%}
    <title>Página Inicial</title>
{%endblock%}

{%block content%}
    <div class="container d-flex">
        <div class="mx-auto my-3 py-5">
            <div class="card text-center mb-3" style="width: 18rem;">
                <div class="card-body">
                <h5 class="card-title">Meu Projeto Django</h5>
                <p class="card-text">Este site foi feito em Django5 e BootStrap.</p>
                <a href="#" class="btn btn-primary">ACESSAR</a>
                </div>
            </div>
        </div>
    </div>
{%endblock%}
```