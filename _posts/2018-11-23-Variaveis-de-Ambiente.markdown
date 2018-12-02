---
layout: post
title:  "Variáveis de Ambiente"
date:   2018-11-23 23:52:46 -0300
categories: 
---
O shell, o interpretador de comandos dos sistemas Unix-like e Linux, permitem a criação de variáveis de ambiente que configuram e/ou controlam a execução de comandos e utilitários. Por convenção, as variáveis de ambiente são criadas em letras maiscúlas. O shell diferencia variáveis em letras maiscúlas e minúsculas. 

O comando *echo* permite exibir o conteúdo de uma variável de ambiente. **Quando a variável nao existe, o shell não exibe nenhuma mensagem de erro.** Nesse caso, é exibida uma linha em branco, como podemos ver no exemplo abaixo. Logo em seguida, um valor é atribuido à variável PORT, e seu valor é exibido. Adicionalmente, o comando *unset* permite remover uma variável de ambiente. 

{% highlight bash %}
# echo $PORT

# PORT=3000
# echo $PORT
3000
# unset PORT
# echo $PORT

# 
{% endhighlight %}

Quando um comando ou utilitário é iniciado em sistemas Unix-like ou Linux, um processo shell filho é criado, que herda as variáveis **exportadas**. O comando *sh* inicia um shell filho. Simplesmente criar uma variável, como podemos ver no exemplo abaixo, não exporta a variável para o shell filho.  

{% highlight bash %}
# PORT=3000
# echo $PORT
3000
# sh
# echo $PORT

# 
{% endhighlight %}

O comando *export* torna a variável disponível para o seu filho, como podemos ver no exemplo abaixo. 

{% highlight bash %}
# PORT=3000
# echo $PORT
3000
# export PORT
# sh
# echo $PORT
3000
# 
{% endhighlight %}

As variáveis de ambiente estão disponíveis dentro do processo que executa o **node**. O comando **process.env** retorna um objeto que contem as variáveis de ambiente, como podemos ver no exemplo abaixo. Para acessar uma unica variável, basta selecionar um dos atributos do objeto. No exemplo abaixo, selecionamos a variável **PORT**, através do comando **process.env.PORT** .

{% highlight bash %}
# PORT=3000
# echo $PORT
3000
# export PORT
# sh
# echo $PORT
3000
# 
# node
> process.env
{ NODE_VERSION: '11.2.0',
  HOSTNAME: '0e91860ce051',
  YARN_VERSION: '1.12.3',
  HOME: '/root',
  PORT: '3000',
  TERM: 'xterm',
  PATH:
   '/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin',
  PWD: '/' }
> process.env.PORT
'3000'
> 
{% endhighlight %}

<br><br>
<sup> 
A versão do Linux é LinuxKit 4.9.125 e a do node é 11.2.0
</sup>