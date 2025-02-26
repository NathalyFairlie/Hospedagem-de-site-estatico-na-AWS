# Hospedando um Site Estático na AWS (S3 & CloudFront)
Tutorial

O ARQUIVO TUTORIAL.HTML CONTEM O TUTORIAL VISUALMENTE MAIS BONITO (BAIXAR E ABRIR NO SEU NAVEGADOR !)

Este tutorial passo a passo irá guiá-lo na criação e hospedagem de um site estático simples utilizando o Amazon S3 (Simple Storage Service) e CloudFront (Content Delivery Network) da AWS, aproveitando o nível gratuito

Projeto 1: Hospedagem de site estático na AWS
Descrição
Neste projeto, você criará e hospedará um site estático simples usando o Amazon S3 e CloudFront, sem nenhum custo (usando o nível gratuito da AWS).
Requisitos
•	Conta na AWS (o nível gratuito oferece 5GB de armazenamento S3 e transferência limitada)
•	Conhecimentos básicos de HTML e CSS
•	Um navegador web
Tutorial passo a passo
1. Criação da conta AWS
1.	Acesse aws.amazon.com
2.	Clique em "Criar uma conta gratuita"
3.	Siga o processo de registro (será necessário fornecer informações de cartão de crédito, porém não haverá cobrança se permanecer dentro dos limites do nível gratuito)
2. Criação de um bucket S3
1.	Acesse o Console AWS e procure por "S3"
2.	Clique em "Criar bucket"
3.	Escolha um nome único para seu bucket (por exemplo: meu-site-estatico-123)
4.	Selecione a região mais próxima de você
5.	Desmarque a opção "Bloquear todo o acesso público"
6.	Marque a caixa reconhecendo que o bucket ficará público
7.	Clique em "Criar bucket"
3. Configuração do bucket para hospedagem de site estático
1.	Clique no bucket que você acabou de criar
2.	Vá para a aba "Propriedades"
3.	Role para baixo até encontrar "Hospedagem de site estático"
4.	Clique em "Editar"
5.	Selecione "Ativar"
6.	Em "Documento de índice", digite "index.html"
7.	Em "Documento de erro", digite "error.html"
8.	Clique em "Salvar alterações"
4. Configuração da política de bucket
1.	Vá para a aba "Permissões"
2.	Em "Política de bucket", clique em "Editar"
3.	Cole a seguinte política (substitua "meu-site-estatico-123" pelo nome do seu bucket):
Código: Json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::meu-site-estatico-123/*"
    }
  ]
}
4.	Clique em "Salvar alterações"
5. Criação dos arquivos HTML básicos
Crie um arquivo index.html com o seguinte conteúdo:
Código: html
<!DOCTYPE html>
<html>
<head>
    <title>Meu Site na Nuvem</title>
    <link rel="stylesheet" type="text/css" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>Bem-vindo ao meu site na nuvem!</h1>
        <p>Este site está hospedado gratuitamente usando AWS S3.</p>
    </div>
</body>
</html>
Crie um arquivo styles.css com o seguinte conteúdo:
Código: css
body {
    font-family: Arial, sans-serif;
    background-color: #f0f8ff;
    margin: 0;
    padding: 0;
}

.container {
    width: 80%;
    margin: 50px auto;
    background-color: white;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0,0,0,0.1);
    text-align: center;
}

h1 {
    color: #0066cc;
}
Crie um arquivo error.html com o seguinte conteúdo:
html
Copy
<!DOCTYPE html>
<html>
<head>
    <title>Erro - Página não encontrada</title>
    <link rel="stylesheet" type="text/css" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>Oops! Página não encontrada</h1>
        <p>A página que você está procurando não existe.</p>
        <a href="index.html">Voltar para a página inicial</a>
    </div>
</body>
</html>
6. Upload dos arquivos para o S3
1.	Na página do seu bucket, vá para a aba "Objetos"
2.	Clique em "Carregar"
3.	Arraste os arquivos index.html, error.html e styles.css ou clique em "Adicionar arquivos" para selecioná-los
4.	Clique em "Carregar"
7. Acessando seu site
1.	Volte para a aba "Propriedades" do seu bucket
2.	Role para baixo até "Hospedagem de site estático"
3.	Você verá o URL do seu site (algo como http://meu-site-estatico-123.s3-website-us-east-1.amazonaws.com)
4.	Clique no link ou copie-o para o navegador
8. (Opcional) Configuração do CloudFront para distribuição global
1.	No Console AWS, procure por "CloudFront"
2.	Clique em "Criar distribuição"
3.	Em "Domínio de origem", selecione o endpoint do seu bucket S3
4.	Mantenha as configurações padrão para a maioria das opções
5.	Em "Objeto raiz padrão", digite "index.html"
6.	Clique em "Criar distribuição"
7.	Aguarde alguns minutos até que o status mude para "Implantado"
8.	Use o "Domínio de distribuição" fornecido para acessar seu site (algo como d1a2b3c4d5e6f7.cloudfront.net)
Conclusão
Parabéns! Você agora tem um site estático hospedado na nuvem AWS, usando serviços gratuitos. Este site pode ser acessado de qualquer lugar do mundo e, com o CloudFront, tem distribuição global de conteúdo.


