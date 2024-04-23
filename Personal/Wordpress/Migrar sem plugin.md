Para sites muito pesados os plugins param de oferecer suporte de forma gratuita. Passo a passo para migrar de forma manual:

1. ==Fazer backup do banco de dados==
	Acessar o phpMyAdmin, caso exista mais de um bd basta abrir o banco e abir o wp_option que lá vai conter a url do site confirmando qual o banco certo.
	Acesse o banco e clique em exportar na barra superior, selecione o método rápido e no formato sql.

2. ==Fazer backup dos arquivos do site==
	Acessar o gerenciador de arquivos e abrir a pasta `public_html`. Conferir em configurações se a opção 'Mostrar arquivos ocultos está selecionado' e selecionar caso não esteja. Após fazer essa validação, clique em seleciona tudo na barra superior, pressione o botão direito e selecione a opção compress. Vai abrir uma janela e nela terão os formatos que podem ser comprimidos, escolha 'Arquivamento Zip'. Compressão finalizada faça download do arquivo.

3. ==Criar novo banco de dados na nova hospedagem==
	Dentro do painel da nova hospedagem vá até 'Banco de Dados MySql' e crie um novo bd inserindo o nome, um usuário e uma senha *Guarde essa senha*.

4. ==Importar backup== 
	Acesse a área do phpMyAdmin, selecione o banco de dados que foi criado anteriormente, clique em importar na superior e selecione o arquivo de backup da antiga hospedagem. Após finalizada a importação acessar a table options e remover o 's' tanto do `siteurl` quanto da `home`. 

5. ==Importar arquivos==
	Agora é o momento de importar através do FTP o arquivos .zip. Crie uma nova conta FTP para conseguir enviar os arquivos. Com essas credenciais abra o filezilla, conecte no servidor usando o IP do FTP e transfira o arquivo. Extraia o .zip dentro da pasta `public_html`. Apague os arquivos zip e default além de mover os arquivos extraído para `/public_html`.

6. ==Atualizar o wp_config==
	Abra o arquivo wp_config e atualize:
	- `define('DB_NAME','nome_do_banco')`  
	- `define('DB_USER','usuario_do_banco')`   
	- `define('DB_PASSWORD','senha_do_banco')`   