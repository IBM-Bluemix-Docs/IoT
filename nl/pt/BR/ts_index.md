---

copyright:
  years: 2016, 2018
lastupdated: "2017-11-03"

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Resolução de problemas do {{site.data.keyword.iot_short_notm}}
{: #ts}

Aqui estão as respostas às perguntas comuns de resolução de problemas sobre o
uso do {{site.data.keyword.iot_full}} no
{{site.data.keyword.Bluemix_notm}}.
{:shortdesc}

## Problema ao acessar a organização do {{site.data.keyword.iot_short_notm}}
{: #access-expiry-problem}

Não é possível efetuar login em uma organização do {{site.data.keyword.iot_short_notm}} de sua propriedade.
{:shortdesc}

Não é possível efetuar login em sua organização do {{site.data.keyword.iot_short_notm}} diretamente usando a URL da organização ou usando `https://internetofthings.ibmcloud.com`.
{: tsSymptoms}

Seu acesso à organização do {{site.data.keyword.iot_short_notm}} pode ter expirado. As organizações do {{site.data.keyword.iot_short_notm}} que foram criadas usando o {{site.data.keyword.Bluemix}} usam perfis de usuário temporários por padrão.
{: tsCauses}

É possível resolver esse problema acessando sua organização do {{site.data.keyword.iot_short_notm}} usando o {{site.data.keyword.Bluemix_notm}} e mudando a configuração de expiração de seu perfil do usuário. Para mudar as configurações de expiração do usuário:

1. No painel do {{site.data.keyword.Bluemix_notm}}, abra o serviço {{site.data.keyword.iot_short_notm}}.
2. Clique em **Membros** na barra de navegação.
3. Clique no ícone **Editar**.
4. Limpe a caixa **O acesso expira** e clique em **Salvar**.
{: tsResolve}

## Problema ao se conectar ao {{site.data.keyword.iot_short_notm}}
{: #connection_problem}

Sua conexão com o {{site.data.keyword.iot_short_notm}} cai ou desconecta inesperadamente.
{:shortdesc}

Ao tentar se conectar ao {{site.data.keyword.iot_short_notm}}, seu dispositivo ou aplicativo recebe um erro.
{: tsSymptoms}

Você pode ter dois dispositivos tentando se conectar com o mesmo clientID e credenciais. Apenas uma conexão exclusiva é permitida por clientID. Não é possível ter duas conexões simultâneas usando o mesmo ID. Os aplicativos podem compartilhar a mesma chave API, mas o MQTT requer que o identificador de cliente seja sempre exclusivo.
{: tsCauses}

É possível resolver esse problema confirmando que você não tem dois dispositivos tentando se conectar usando as mesmas credenciais.
{: tsResolve}

## O dispositivo desconecta-se de forma intermitente do {{site.data.keyword.iot_short_notm}}
{: #disconnection_problem}

Sua conexão de dispositivo com o {{site.data.keyword.iot_short_notm}} cai de forma intermitente inesperadamente.
{:shortdesc}

Um dispositivo que está conectado ao serviço do {{site.data.keyword.iot_short_notm}} é desconectado de forma intermitente. O dispositivo reconecta-se, mas é desconectado inesperadamente mais uma vez após algum tempo.
{: tsSymptoms}

Pode ser que ao conectar-se você esteja usando um valor para uma opção de ping MQTT que é muito baixa, o que faz parecer que a conexão atingiu o tempo limite. Por exemplo, se o cliente MQTT estiver configurado incorretamente, os pings não serão recebidos em tempo hábil e a conexão é fechada.
{: tsCauses}

É possível corrigir este problema, confirmando se você configurou corretamente o ping e os parâmetros de KeepAlive para sua conexão.   
{: tsResolve}

