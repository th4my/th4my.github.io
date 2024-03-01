---
layout: post
title:  "Criando um blog no Github Pages com o Jekyll"
date:   2024-02-28 16:37:29 -0400
categories: jekyll github
---
O Jekyll é um gerador de sites que pega o código e usa layouts para criar um site estático, sendo possível ajustar a aparência do site, os URLs e os dados exibidos na página. O GitHub Pages foi desenvolvido pelo Jekyll, então podemos criar um site pelo GitHub!! Ok, mas qual a vantagem? É de grátis. ;D

Pré-requisitos para instalação do Jekyll:
- Ruby versão 2.5.0 ou superior
- Ruby Gems
- GCC e Make

### Instalação:
1. Instale os pré-requisitos.
2. Instale o Jekyll e o bundle gems: 
> $ gem install jekyll bundler
3. Acesse o diretório do seu projeto no Github:
> $ cd seu-projeto.github.io
4. Crie um novo site Jekyll (no caso o . indica para criar no dir atual):
> $ jekyll new . 
5. Construa o site e deixe ele disponível localmente:
> $ bundle exec jekyll serve
6. Acesse o seu site pela url: http://127.0.0.1:4000/

* Se der algum erro do tipo 'bundler: failed to load command: jekyll', adicione o webrick: `$ bundle add webrick` (esse comando adiciona o webrick ao Gemfile) e depois: `$ bundle install && bundle update`.



### Instalando a skin dark do tema Minima do Jekyll:
Eu estava procurando um tema escuro para o meu blog, mas reparei que vários temas estava desatualizados ou não faziam integração com o Github Pages. Então descobri que o tema Minima possui skins, mas atualmente ela ainda está em beta e ainda não foi lançado como uma versão estável, estando disponível apenas via repositório e para isso é preciso usar o plugin `'jekyll-remote-theme'`. 
Então resolvi usar a versão beta mesmo no meu blog. Para isso eu copiei o diretório `_sass` do repositório do github e adicionei ao meu código. Depois editei o `Gemfile` comentando a linha gem "minima", "~> 2.5" para gem "minima". Editei o Gemfile de modo que ficou parecido com isso:
{% highlight ruby %}
#gem "minima", "~> 2.5"
gem "minima"

gem "github-pages", group: :jekyll_plugins
# If you have any plugins, put them here!
group :jekyll_plugins do
  gem "jekyll-feed", "~> 0.12"
end

gem "webrick", "~> 1.8"
{% endhighlight %}



Edite o arquivo `_config.yml` e adicione o seu skin favorito (auto, classic, dark, solarized-dark, solarized-light, solarized) e adicione também o `remote_theme: jekyll/minima`:
{% highlight ruby %}
# Build settings
theme: minima
minima:
  skin: dark
  date_format: "%b %-d, %Y"

plugins:
  - jekyll-feed

remote_theme: jekyll/minima
{% endhighlight %}

Depois suba o projeto no Github:
> $ git add -A

> $ git commit -m "add dark Jekyll theme"

> $ git push

É isso ai, é nois que voa bruxão!!! 

### Fontes:
[jekyll-docs][jekyll-docs]

[retired][retired]

[jekyll-docs]: https://jekyllrb.com/docs/home
[retired]: https://retired.re-ynd.com/2024/dark-theme-in-jekyll/



[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/