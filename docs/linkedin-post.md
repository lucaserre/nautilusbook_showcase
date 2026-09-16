# LinkedIn Post Draft

Eu comecei querendo criar um diário de livros.

Acabei estudando, na prática, por que “funciona na minha máquina” está muito longe de significar “está seguro”.

Se trata do meu SaaS: **NautilusBook**.

A ideia inicial era simples: registrar leituras, notas e anotações por uma conversa no WhatsApp, usando uma IA rodando localmente.

Mas os testes começaram a mostrar problemas muito mais interessantes do que a feature em si.

Um webhook duplicado gerava entregas repetidas. O WhatsApp passou a identificar alguns usuários por `@lid`, e tratar aquilo como telefone criou um problema de identidade. Retries exigiram idempotência. O contexto da IA chegou a aplicar alterações no livro errado. Uma única mensagem podia falar de dois livros. Uploads precisavam ser tratados como conteúdo não confiável. JWT sozinho não resolvia logout e revogação. E até uma variável de ambiente com o tipo errado fez o Ollama rejeitar todas as requisições com HTTP 400.

Cada falha virou uma regra, um teste ou um controle.

Hoje o projeto já envolve FastAPI, PostgreSQL, Alembic, Docker, Ollama/Qwen3, WAHA, structured outputs, fila/worker, autenticação com sessões revogáveis, refresh token rotativo, rate limiting, validação de uploads, backups e um threat model que continua evoluindo.

O aprendizado que mais me marcou foi este:

**segurança não entrou como uma checklist no final. Ela apareceu toda vez que uma suposição sobre o sistema quebrou.**

“E se a mensagem chegar duas vezes?”

“E se esse identificador não for um telefone?”

“E se a IA estiver confiante e errada?”

“E se um token roubado for reutilizado?”

“E se o arquivo não for aquilo que a extensão diz?”

Esse é exatamente o tipo de raciocínio que quero aprofundar profissionalmente em **Application Security e Threat Hunting**.

O desenvolvimento é **assistido por IA**. Uso o ChatGPT como apoio de implementação, arquitetura, debugging e documentação. Requisitos, decisões de produto, execução dos testes, reprodução dos bugs e validação final das mudanças continuam sendo conduzidos por mim. E várias vezes os testes provaram que uma solução aparentemente correta precisava ser refeita — o que, para mim, é uma das partes mais valiosas do processo.

Como o NautilusBook pode se tornar um produto comercial, o core permanece privado. Em vez de abrir o SaaS inteiro, publiquei um **engineering & security showcase** com arquitetura, threat model, decisões de AppSec, estratégia de testes e aprendizados técnicos.

https://github.com/lucaserre/nautilusbook_showcase

Se você trabalha com AppSec, segurança ofensiva/defensiva ou engenharia de software, tenho uma pergunta:

**qual seria a primeira coisa que você tentaria quebrar nessa arquitetura?**

#ApplicationSecurity #CyberSecurity #AppSec #ThreatHunting #Python #FastAPI #Docker #PostgreSQL #LLMSecurity #ThreatModeling
