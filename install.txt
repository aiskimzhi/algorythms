1. Скачиваем Composer https://getcomposer.org/ 
Если у вас уже установлен Composer, обновите его при помощи composer self-update. 

2. После установки Composer устанавливать Yii можно запустив следующую команду в папке доступной через веб:
	composer global require "fxp/composer-asset-plugin:~1.1.1"
	composer create-project --prefer-dist yiisoft/yii2-app-basic dir.name 2.0.6 

3. Добавляем приложение в фаил C:\Windows\System32\drivers\etc\hosts
	127.0.0.1	localhost
	::1			localhost
	127.0.0.1	dir.name
	127.0.0.1	www.dir.name 

4. Добавляем приложение в фаил D:\ProgramFiles\xampp\apache\conf\extra\httpd-vhosts
	<VirtualHost *:80>
		ServerAdmin asi@localhost
		DocumentRoot "D:/server/dir.name/basic/web"
		ServerName dir.name
		<Directory "D:/server/dir.name/basic/web">
			ServerSignature Off
			Options Indexes FollowSymLinks IncludesNoExec
			AllowOverride All
			Require all granted
		</Directory>
	</VirtualHost> 

5. В папку dir.name/web кладем фаил .htaccess
	RewriteEngine on

	# If a directory or a file exists, use the request directly
	RewriteCond %{REQUEST_FILENAME} !-f
	RewriteCond %{REQUEST_FILENAME} !-d

	# Otherwise forward the request to index.php
	RewriteRule . index.php 

6. Открываем фаил config/web.php и настраиваем урлы
	$config = [
		//настройки по умолчанию
		'user' => [],
		'urlManager' => [
			'enablePrettyUrl' => true, 
			'showScriptName' => false,
			'enableStrictParsing' => false,
		],
		//дальше настройки по умолчанию 
	]; 
