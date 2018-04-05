PMA Scripts
===========

Scripts para acesso ao PMA


Exemplo de uso:
---------------

    pma_token
    pma_create_day && pma_projects | grep RH | cut -d "|" -f 3 | xargs pma_tasks | cut -d "|" -f2 | xargs pma_create_task -e 60
    pma_logout


pma_token
---------

Faz login no PMA e guarda token no arquivo *$HOME/.pma_token*. Demais scripts usarão este arquivo para obter o token.
Caso usuário seja omitido, utiliza *$USER*. Pede a senha durante a execução.

    pma_token [username]


pma_logout
---------

Faz o logout do PMA. Pede a senha durante a execução. Caso usuário seja omitido, utiliza *$USER*.

    pma_logout [username]

pma_projects
---------

Lista projetos vinculados a você.

    pma_projects

pma_tasks
---------

Lista atividades vinculadas ao(s) projeto(s) passados por parâmetro.

    pma_tasks <projectId> [projectId ...]

pma_create_day
--------------

Cria apontamento diário. Caso não seja passado nenhum parâmetro, cria para o dia corrente, das 09:00 às 18:00 com 01:00 de intervalo.

     pma_create_day [options]
        -h                 : This help
        -d <date>          : Date to create (yyyy-MM-dd). Default value is today (date +'%F')
        -s <start time>    : Start time (HH:mm). Default value is '09:00'
        -e <end time>      : End time (HH:mm). Default value is '18:00'
        -i <interval time> : Interval time (HH:mm). Default value is '01:00'

pma_create_task
---------------

Cria apontamento em atividade. Caso o data e esforço sejam omitidos, cria para o dia corrente com 08:00 de esforço. Status da atividade padrão é *working*.
Deve-se passar o id da atividade e opcionalmente sua descrição (caso omitida esta, usa *Devel* por padrão).

    pma_create_task [options] <taskid> [description]
       -h                 : This help
       -d <date>          : Date to create (yyyy-MM-dd). Default value is today (date +'%F')
       -e <effort time>   : Effort time (minutes). Default value is 480 (8 * 60)
       -s <status>        : Status ('working' or 'concluded'). Default value is 'working'
    Description is not required. Default value is 'Devel'.

pma_list
--------

Lista suas atividades nos dias especificados. Caso omitida a data, utiliza data corrente.

    pma_list [date] [date] ...
