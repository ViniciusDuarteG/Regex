# Regex


Regex é uma ferrementa super validada em analise de dados. Essa ferramenta pode ser utilizada em diversos ambientes, e muito comum em textos. 

## Limpar textos
Pode se extrair informações importantes de textos, e com esses mesmos dados serem implementados em variáveis, listas, tuplas, etc.; 

- Remover tudo exceto números

      re.sub(r'\d', '', texto)

- Remover espalos duplicados 

      re.sub(r'\s+', ' ', texto)

- Deixar somente letras 

      re.sub(r'[^a-zA-Z]', '', texto)


## Validação de formulários 
Técnica necessáriamente utilizada, principalmente se for juntar com Flask para desenvolvimento web
Exemplos:
- E-mails

      ^[\w\.-]+@[\w\.-]+\.\w{2,}$

- CPFs 

      re.findall(r'\d{3}\.\d{3}\.\d{3}\-\d{2}', texto)

- Telefone
  
        padrao_tel = r'(\(\d{2}\)\s?\d{5}-\d{4}|\d{2}\s\d{5}-\d{4}|\d{5}-\d{4}|\d{9}|\(\d{2}\)\s9\s\d{4}-\d{4})'
        resultado = re.findall(padrao_tel, texto)

## Extrair informações de texto
Web Scraping, Logs de sistema, Processar PDFs, organizar dados 

- Extrair URLS 

      https?://[^\s]+

- Pegar nomes entre aspas 

      "([^"]+)"

- Pegar valores reais    

      R\$\s?\d+(\.\d{3})*,\d{2}

- Extrair horas 

      \d{2}:\d{2}

## Substituir informações sensiveis 

Essa parte é importante, principalmente para gerar PDFs e documentos publicos 
- Mascara de CPF
  
        re.sub(r'\d{3}\.\d{3}\.\d{3}-', '***.***.***-', cpf)

- Mascara de telefone 

      re.sub(r'.+(\d{4})$', r'****-\1', tel)

## Busca de padrões complexos
- Números negativos e positivos 

      -?\d+(\.\d+)?

- Palavras com letras maiusculas 

      \b[A-Z][a-z]+

- Tags HTML 

       <[^>]+>

## Criar filtros
Muito utilizado, principalmente para bots e automações, ou sistemas de buscas

Exemplo: pegar mensagens que contenham números, mas não CPF:

    ^(?!.*\d{3}\.\d{3}\.\d{3}-\d{2}).*\d
