# Catálogo de projetos

[Apresentação](README.md) · [Experiência](docs/EXPERIENCIA.md) · [Auditoria](docs/AUDITORIA.md)

Seis repositórios examinados em 20/10/2026. As evidências apontam para os commits analisados; os links de entrada acompanham a versão atual. Complexidade é uma estimativa relativa ao escopo do código, sem atribuir senioridade ou homologação em produção.

## Navegação por área

- **Backend e APIs .NET:** [estacao-climatica-csharp](#estacao-climatica-csharp) — destaque principal.
- **Bancos de dados:** [Oracle-Database](#oracle-database) — destaque.
- **Sistemas web e frontend:** [anvmano.github.io](#anvmano-github-io) — destaque.
- **Eletrônica e integrações:** [estacao-climatica](#estacao-climatica) — complementar.
- **Eletrônica e aquisição de dados:** [SensorsController](#sensorscontroller) — complementar.
- **Automação de iluminação:** [LightingController](#lightingcontroller) — demais projetos, ferramenta de escopo específico.

## estacao-climatica-csharp

**Estação Climática em C#/.NET** · [Repositório](https://github.com/anvmano/estacao-climatica-csharp) · Destaque principal

**Problema e objetivo:** transformar históricos de sensores em consultas e visualizações, movendo processamento do dashboard original para um backend C# e oferecendo clima público sem login.

**Funcionalidades implementadas:**

- API para ambientes, última medição, histórico, séries, resumo, qualidade do ar estimada, eventos solares, alertas, comparações e exportações.
- Dashboard de Estação, Sala, Quarto e Aquário, com estatísticas, indicadores de qualidade, gráficos, tabelas e exportação PDF/JSON no navegador.
- Consulta pública por CEP, cidade brasileira ou coordenadas, com previsão de 15 dias e indicadores ambientais.
- Verificação de Firebase ID token e lista de e-mails autorizados para rotas internas; health e clima público anônimos.
- Assistente com cálculos locais em C# e integração opcional Gemini pelo backend, desativada na configuração padrão.
- Cache curto por URL e novas tentativas com espera progressiva na leitura do Firebase.

**Tecnologias e dependências:** C#, .NET 8 (`net8.0`), ASP.NET Core Controllers, `HttpClient`, `System.Text.Json`, Firebase Realtime Database por REST, Firebase Authentication, JavaScript, HTML/CSS e Chart.js; html2canvas/jsPDF para PDF. Testes: xUnit, Microsoft.NET.Test.Sdk, Microsoft.Playwright e coverlet.collector. Não há dependência de Entity Framework ou NHibernate neste projeto.

**Arquitetura e estrutura:** `Domain` contém contratos/modelos; `Application`, serviços, regras e abstrações; `Infrastructure`, implementações HTTP, autenticação e repositório Firebase; `Web`, controllers e arquivos estáticos em `wwwroot`. As referências dos `.csproj` e os registros em `Program.cs` comprovam a separação e a injeção de dependências. Isso não atribui automaticamente DDD, microsserviços ou todas as regras de Clean Architecture ao projeto.

**Integrações:** Firebase, BrasilAPI com alternativa ViaCEP, Open-Meteo Forecast/Air Quality/Geocoding e Gemini opcional. O backend de leitura Firebase não acrescenta credencial à requisição: regras e acesso ao banco precisam ser definidos na implantação, conforme o [registro de segurança](docs/SEGURANCA.md).

**Qualidade e testes:** há testes de serviços, controllers, cliente HTTP, autenticação, estrutura do frontend e navegador. A comparação de paridade ao vivo só ocorre quando `RUN_LIVE_PARITY=1`. As suítes não foram executadas nesta auditoria; o número de testes aprovados relatado no README original não foi adotado como resultado desta entrega. Não foi encontrado workflow versionado em `.github/workflows`.

**Instalação e execução documentadas:** .NET SDK 8; `dotnet restore EstacaoClimatica.sln` e `dotnet run --project src/EstacaoClimatica.Web/EstacaoClimatica.Web.csproj --launch-profile http`. O perfil usa `http://localhost:5285`. O painel interno exige configuração do próprio Firebase e dos usuários autorizados. Consulte o [guia completo](https://github.com/anvmano/estacao-climatica-csharp/blob/main/docs/README.md) antes de configurar.

**Estado e complexidade:** funcionalidades implementadas, em evolução; complexidade média-alta dentro do conjunto, pelo processamento, integrações, autenticação e testes. Não foi identificada URL de demonstração pública da implantação .NET. A demonstração web é outra implementação.

**Documentação e recursos visuais:** documentação detalhada em `docs/`, com contratos da API e limitações; falta README na raiz do commit analisado. Há ícones da aplicação, sem capturas de tela versionadas identificadas.

**Competências e diferenciais:** organização de backend, contratos HTTP, processamento de séries temporais, isolamento do acesso externo, validação de consultas e testes em diferentes níveis.

**Melhorias recomendadas:** criar uma entrada curta na raiz; registrar validação reproduzível das suítes; revisar acesso Firebase e tratamento operacional de falhas; esclarecer que App Check está apenas modelado na versão .NET, sem validação implementada. O assistente concentra mais de duas mil linhas no arquivo principal, um ponto de manutenção a acompanhar conforme crescer.

**Evidências no commit analisado:** [projetos e referências](https://github.com/anvmano/estacao-climatica-csharp/tree/2dd5fe9a43c697f680ad8463a67d4ffb4bd8f52a/src) · [composição e proteção das rotas](https://github.com/anvmano/estacao-climatica-csharp/blob/2dd5fe9a43c697f680ad8463a67d4ffb4bd8f52a/src/EstacaoClimatica.Web/Program.cs) · [consultas HTTP](https://github.com/anvmano/estacao-climatica-csharp/blob/2dd5fe9a43c697f680ad8463a67d4ffb4bd8f52a/src/EstacaoClimatica.Web/Controllers/ClimateQueryController.cs) · [cache e novas tentativas](https://github.com/anvmano/estacao-climatica-csharp/blob/2dd5fe9a43c697f680ad8463a67d4ffb4bd8f52a/src/EstacaoClimatica.Infrastructure/Firebase/FirebaseDataSource.cs) · [clima público](https://github.com/anvmano/estacao-climatica-csharp/blob/2dd5fe9a43c697f680ad8463a67d4ffb4bd8f52a/src/EstacaoClimatica.Infrastructure/External/PublicWeatherService.cs) · [dependências dos testes](https://github.com/anvmano/estacao-climatica-csharp/blob/2dd5fe9a43c697f680ad8463a67d4ffb4bd8f52a/tests/EstacaoClimatica.Tests/EstacaoClimatica.Tests.csproj) · [cenários de teste](https://github.com/anvmano/estacao-climatica-csharp/tree/2dd5fe9a43c697f680ad8463a67d4ffb4bd8f52a/tests/EstacaoClimatica.Tests)

## Oracle-Database

**Oracle Database: guias e biblioteca DBA** · [Repositório](https://github.com/anvmano/Oracle-Database) · Destaque

**Problema e objetivo:** organizar conhecimento de administração Oracle e facilitar a localização de procedimentos e scripts por tarefa ou sintoma.

**Conteúdo implementado:** 82 tutoriais segundo o índice do acervo; biblioteca cuja contagem foi conferida nos arquivos: 77 consultas de diagnóstico, 7 intervenções e 6 geradores de DDL, além do inicializador; 20 roteiros de solução de problemas. Os temas incluem sessões, bloqueios, espaço, memória, estatísticas, RMAN, Data Pump, Data Guard, privilégios e OCI.

**Tecnologias:** Oracle Database, SQL, PL/SQL, SQL*Plus, RMAN e comandos Shell/Bash nos guias de Linux; Oracle Linux e OCI como ambientes documentados. Python é usado nos verificadores do acervo, sem caracterizar uma aplicação backend Python.

**Estrutura e organização:** Markdown na raiz, roteiros em `solucao-de-problemas/`, scripts em `scripts/diagnostico/`, `scripts/manutencao/` e `scripts/geradores/`, verificadores em `tests/`. Não é uma aplicação web ou API. A biblioteca declara Oracle Database/SQL*Plus 19c; tutoriais de outras versões mantêm contexto próprio.

**Qualidade e diferenciais:** separação por efeito, cabeçalhos com contexto/privilégios, binds e erros propagados. Na amostra lida, `bloqueadores.sql` associa instâncias; `recompilar_objeto.sql` confere banco/container, usuário, tipo e confirmação; `extrair_ddl_objeto.sql` usa `DBMS_METADATA` e apenas produz DDL para revisão. Essas observações não equivalem a homologar todos os scripts em Oracle.

**Testes:** verificadores Python de estrutura, links e regressões; há cenários simulados e um roteiro Oracle. Não foram executados nesta auditoria. SQLite e ferramentas simuladas não comprovam execução do dialeto Oracle. Nenhum workflow de CI foi encontrado no snapshot.

**Uso e dependências:** começar pelo [catálogo SQL](https://github.com/anvmano/Oracle-Database/blob/main/scripts/CATALOGO.md), ler requisitos do arquivo e preparar uma sessão dedicada conforme a [biblioteca](https://github.com/anvmano/Oracle-Database/blob/main/scripts/README.md). Os scripts têm efeitos e ambientes diferentes; não há execução geral do diretório. Mídias e licenças Oracle não são distribuídas pelo portfólio.

**Estado e complexidade:** acervo organizado e disponível para consulta, com complexidade média-alta de domínio operacional. Revisão documental e execução real são estados diferentes: a documentação registra que instalação, patch, backup e recuperação não foram executados na revisão descrita. Não há demonstração executável pública identificada.

**Documentação e imagens:** README raiz abrangente, catálogos, contribuição, licença própria e limitações explícitas. Existe uma imagem de banco de dados; não é evidência de execução nem captura funcional necessária ao portfólio.

**Competências demonstradas:** SQL/PLSQL, leitura de metadados, organização de procedimentos e controle de escopo das intervenções. A experiência profissional de DBA é declarada separadamente no currículo.

**Melhorias recomendadas:** manter a biblioteca como fonte canônica, facilitar o percurso inicial para recrutadores e, quando houver ambiente próprio, anexar evidências sanitizadas de execução com versão e cenário exatos. Preservar as ressalvas dos guias históricos.

**Evidências:** [índice e limites](https://github.com/anvmano/Oracle-Database/blob/93d72004e68216b00bc67afe6e2c977b3a701f6a/README.md) · [biblioteca](https://github.com/anvmano/Oracle-Database/tree/93d72004e68216b00bc67afe6e2c977b3a701f6a/scripts) · [bloqueadores](https://github.com/anvmano/Oracle-Database/blob/93d72004e68216b00bc67afe6e2c977b3a701f6a/scripts/diagnostico/bloqueadores.sql) · [recompilação com verificações](https://github.com/anvmano/Oracle-Database/blob/93d72004e68216b00bc67afe6e2c977b3a701f6a/scripts/manutencao/recompilar_objeto.sql) · [gerador de DDL](https://github.com/anvmano/Oracle-Database/blob/93d72004e68216b00bc67afe6e2c977b3a701f6a/scripts/geradores/extrair_ddl_objeto.sql) · [verificadores](https://github.com/anvmano/Oracle-Database/tree/93d72004e68216b00bc67afe6e2c977b3a701f6a/tests)

## anvmano-github-io

**Dashboard climático web** · Nome original: `anvmano.github.io` · [Repositório](https://github.com/anvmano/anvmano.github.io) · [Demonstração](https://anvmano.github.io/) · Destaque

**Problema e objetivo:** apresentar históricos climáticos e do aquário no navegador e permitir consultas públicas sem exigir acesso aos sensores internos.

**Implementado:** abas de Estação, Sala, Quarto e Aquário; seleção de data, estatísticas, tabelas, gráficos sincronizados e zoom; qualidade das leituras, heatmaps e ciclo solar; exportações PDF/JSON; login Google; modo público por CEP, cidade ou localização, com previsão de 15 dias; assistente com integração Firebase AI Logic.

**Tecnologias e dependências:** JavaScript, HTML, CSS, Chart.js, Firebase App/Auth/Realtime Database, App Check condicionado à configuração e Firebase AI Logic; html2canvas/jsPDF para PDF. Ferramentas em `package.json`: ESLint, Prettier, Playwright Core, axe-core e PDF.js. Algumas bibliotecas de produção vêm de CDN; as versões do runtime devem ser conferidas separadamente das dependências de desenvolvimento.

**Arquitetura e estrutura:** aplicação estática com módulos por responsabilidade em `scripts/`, `styles/` e fachadas/globais em `window`. `main.js` coordena inicialização e modos público/interno. Firebase é consultado diretamente no navegador. Não há servidor ASP.NET neste repositório.

**Integrações:** BrasilAPI, ViaCEP e Open-Meteo Forecast/Air Quality/Geocoding no modo público; Firebase no fluxo interno. App Check tem inicialização no código, mas isso não comprova enforcement remoto. A lista de usuários na interface não substitui regras de autorização do banco.

**Qualidade e testes:** scripts de sintaxe e referências HTML/CSS, assistente, relatórios, qualidade de dados, acessibilidade, tabelas e interface; cenários de navegador com Playwright Core e axe. Existência verificada, sem execução nesta auditoria. Não foi encontrado workflow de CI nem `.gitignore` no commit analisado.

**Execução documentada:** servir a raiz como site estático, por exemplo com `python -m http.server 8080`. Para ferramentas de desenvolvimento, instalar as dependências de `package.json`; `npm run validate`, `npm run lint` e testes específicos estão no [guia](https://github.com/anvmano/anvmano.github.io/blob/main/docs/README.md). Firebase exige configuração própria e regras adequadas.

**Estado e complexidade:** implementado e em evolução; complexidade média-alta para um frontend estático, pelas regras, visualizações e integrações. A demonstração respondeu HTTP 200, com título “Estação Climática”; isso não valida login, consultas externas ou dados internos em produção.

**Documentação e recursos visuais:** guia detalhado em `docs/README.md`, arquitetura e regras; falta README na raiz. Há ícones e relatório HTML de análise, sem capturas de tela versionadas identificadas. A demonstração é o recurso visual disponível.

**Competências e diferenciais:** visualização e transformação de dados, integração no navegador, carregamento sob demanda, responsividade e cenários de acessibilidade.

**Melhorias recomendadas:** adicionar README de entrada, criar `.gitignore` para dependências/artefatos locais mediante autorização e registrar capturas sanitizadas. A dependência de globais e da ordem dos scripts merece atenção na manutenção.

**Evidências:** [guia](https://github.com/anvmano/anvmano.github.io/blob/c4d5b5e624f0f5fe7c82742e788f3ddcde0da4e0/docs/README.md) · [orquestração](https://github.com/anvmano/anvmano.github.io/blob/c4d5b5e624f0f5fe7c82742e788f3ddcde0da4e0/scripts/main.js) · [APIs públicas](https://github.com/anvmano/anvmano.github.io/blob/c4d5b5e624f0f5fe7c82742e788f3ddcde0da4e0/scripts/external/external-weather-service.js) · [Firebase e App Check](https://github.com/anvmano/anvmano.github.io/blob/c4d5b5e624f0f5fe7c82742e788f3ddcde0da4e0/scripts/firebase-service.js) · [dependências e comandos](https://github.com/anvmano/anvmano.github.io/blob/c4d5b5e624f0f5fe7c82742e788f3ddcde0da4e0/package.json) · [verificadores](https://github.com/anvmano/anvmano.github.io/tree/c4d5b5e624f0f5fe7c82742e788f3ddcde0da4e0/tools)

## estacao-climatica

**Estação climática ESP32** · [Repositório](https://github.com/anvmano/estacao-climatica) · Complementar

**Problema e objetivo:** coletar temperatura/umidade, manter data e hora na estação e disponibilizar histórico e consultas pelo Telegram.

**Implementado:** leitura DHT22 e sensação térmica, RTC DS3231 sincronizado por NTP, histórico climático na hora cheia, rotina de horários solares, comandos Telegram para remetentes autorizados e visitantes, consultas por CEP/localização e alerta após o amanhecer. Gravações falhas ou posteriores a pendências podem ir para fila LittleFS com novas tentativas e destino determinístico.

**Tecnologias e dependências:** C++/Arduino para ESP32, ArduinoJson, DHT sensor library, RTClib, Firebase ESP32 Client, UniversalTelegramBot, NTPClient, LittleFS e Preferences. Serviços: OpenWeather, Sunrise-Sunset e Nominatim/OpenStreetMap. Firebase usa a biblioteca `FirebaseESP32`, diferente do REST direto dos outros dois firmwares.

**Estrutura e arquitetura:** sketch `estacao_climatica.ino` e abas para utilitários, conectividade, sensores, APIs, Firebase, Telegram, tarefas e fila; estado compartilhado e execução cooperativa por `setup()`/`loop()`. O modelo de `secrets.h` é versionado sem credenciais reais.

**Qualidade, estado e complexidade:** implementado e documentado, complexidade média por hardware, bot, agenda e persistência. README abrangente, pinagem e instruções Arduino IDE/CLI; sem suíte automatizada ou CI no snapshot. A compilação descrita no README é um registro anterior, não repetido aqui.

**Instalação e operação:** requer ESP32, DHT22, DS3231, LittleFS, bibliotecas e serviços próprios. O nome da pasta do sketch deve seguir o [guia de instalação](https://github.com/anvmano/estacao-climatica/blob/main/README.md); preparar pasta, credenciais e bibliotecas antes de compilar.

**Limitações e melhorias:** rede pode bloquear o loop; agendas dependem do minuto previsto; horários solares podem ficar desatualizados; fila limitada pode bloquear em registro inválido. APIs HTTPS usam `setInsecure()`, enquanto o cliente Telegram configura certificado raiz. Validar TLS, perda de energia, retenção e ocupação de flash com hardware real antes de ampliar o firmware.

**Competências e diferencial:** integração de sensor, relógio, bot e banco; tratamento de falhas de leitura e reaproveitamento do destino nas novas tentativas. A fila não garante ausência de perda em qualquer falha.

**Imagens e demonstração:** sem fotos, esquemas completos, capturas ou demonstração pública do firmware identificados. O dashboard web é um consumidor relacionado, sem comprovar o funcionamento físico desta placa.

**Evidências:** [sketch e bibliotecas](https://github.com/anvmano/estacao-climatica/blob/cc28a94828c8837fd1f625945856872f0f046324/estacao_climatica.ino) · [DHT22](https://github.com/anvmano/estacao-climatica/blob/cc28a94828c8837fd1f625945856872f0f046324/03_Sensors.ino) · [Firebase](https://github.com/anvmano/estacao-climatica/blob/cc28a94828c8837fd1f625945856872f0f046324/05_Firebase.ino) · [Telegram](https://github.com/anvmano/estacao-climatica/blob/cc28a94828c8837fd1f625945856872f0f046324/06_Telegram.ino) · [agenda](https://github.com/anvmano/estacao-climatica/blob/cc28a94828c8837fd1f625945856872f0f046324/07_Tasks.ino) · [fila](https://github.com/anvmano/estacao-climatica/blob/cc28a94828c8837fd1f625945856872f0f046324/08_FirebaseQueue.ino)

## SensorsController

**Monitoramento de ambiente e água** · [Repositório](https://github.com/anvmano/SensorsController) · Complementar

**Problema e objetivo:** reunir leituras do ar e aquário e enviar históricos ao Firebase, preservando operações pendentes localmente quando possível.

**Implementado:** BME680 para temperatura/umidade/pressão; MQ135 para estimativas de gases após calibração; DS18B20 para temperatura da água; TDS com compensação de temperatura; turbidez e pH com amostragem e conversão; estado por sensor; coleta horária por categoria; diagnóstico inicial; fila FIFO LittleFS e HTTP `PUT` em destinos determinísticos.

**Tecnologias e dependências:** C++/Arduino, ESP32/WEMOS D1 R32, Adafruit BME680, MQUnifiedsensor, OneWire, DallasTemperature, ArduinoJson, NTPClient, Time, HTTPClient, LittleFS e Preferences. Pinagem, limites e calibração em `config.h`; credenciais no `secrets.h` local.

**Estrutura e arquitetura:** sketch principal e abas de utilitários, conectividade, sensores do ar/aquário, JSON, tarefas e fila. Aquisição separada da iluminação, tratada no LightingController. REST direto, sem SDK Firebase específico.

**Qualidade, estado e complexidade:** implementado, complexidade média por sensores analógicos, calibração e armazenamento. README detalhado e explícito sobre falhas; sem suíte automatizada ou CI. Compilação relatada na documentação não repetida nesta auditoria.

**Instalação e operação:** preparar WEMOS D1 R32, sensores, adequação elétrica, bibliotecas e `secrets.h`; seguir o [guia Arduino IDE/CLI](https://github.com/anvmano/SensorsController/blob/main/README.md). Calibrações e tensões devem corresponder à montagem real; leitura de código não valida precisão física.

**Limitações:** fila de até 100 itens/64 KiB e possíveis perdas na recuperação. Temporário com JSON válido não comprova cópia completa; no boot o principal é removido antes da promoção do temporário. Falha ao abrir o principal também pode impedir a preservação de itens antigos. TLS usa `setInsecure()` e token na URL. Gases e turbidez são estimativas dependentes da calibração.

**Competências e diferencial:** múltiplos sensores, mediana em pH/turbidez, compensação TDS, sinalização de indisponibilidade e persistência com novas tentativas. Não se atribui certificação às medições ou garantia transacional à fila.

**Melhorias recomendadas e recursos visuais:** testar perda de energia e falhas de armazenamento; rever TLS, validade das leituras e calibração; adicionar esquema elétrico e evidências sanitizadas quando disponíveis. Não foram encontradas fotos, capturas ou demonstração física versionada.

**Evidências:** [bibliotecas e inicialização](https://github.com/anvmano/SensorsController/blob/f6840dbf34d2e15f90c4a4ff4429f6863aa5cdd5/SensorsController.ino) · [sensores do ar](https://github.com/anvmano/SensorsController/blob/f6840dbf34d2e15f90c4a4ff4429f6863aa5cdd5/03_AirSensors.ino) · [aquário e conversões](https://github.com/anvmano/SensorsController/blob/f6840dbf34d2e15f90c4a4ff4429f6863aa5cdd5/04_AquariumSensors.ino) · [JSON e estados](https://github.com/anvmano/SensorsController/blob/f6840dbf34d2e15f90c4a4ff4429f6863aa5cdd5/05_Firebase.ino) · [fila e recuperação](https://github.com/anvmano/SensorsController/blob/f6840dbf34d2e15f90c4a4ff4429f6863aa5cdd5/07_FirebaseQueue.ino) · [configuração](https://github.com/anvmano/SensorsController/blob/f6840dbf34d2e15f90c4a4ff4429f6863aa5cdd5/config.h)

## LightingController

**Iluminação de aquário por ciclo solar** · [Repositório](https://github.com/anvmano/LightingController) · Demais projetos: automação de escopo específico

**Problema e objetivo:** ajustar a iluminação de aquário plantado ao longo do dia usando horários solares do Firebase.

**Implementado:** leitura solar REST, relógio NTP, transições de brilho por interpolação *smoothstep*, cores em cinco fileiras e relé na janela do zênite. Mantém LEDs/relé desligados sem relógio válido ou primeira carga solar válida; preserva horários carregados quando uma nova consulta falha.

**Tecnologias:** C++/Arduino, ESP32/WEMOS D1 R32, FastLED, NeoPixel, ArduinoJson, NTPClient, Time e HTTPClient. Configura 125 LEDs em cinco fileiras de 25 e relé da luz branca. Não lê sensores nem produz os horários solares consumidos.

**Estrutura e arquitetura:** sketch principal, `config.h`, exemplo de credenciais e cinco abas para tempo, rede, dados solares, atuadores e tarefas. Loop cooperativo e configuração estática.

**Qualidade, estado e complexidade:** implementação de escopo definido, complexidade baixa-média no conjunto. README explica algoritmo, pinagem, dependências, instalação, diagnóstico e limites. Sem testes automatizados ou CI; compilação registrada não repetida aqui. A exposição menor reflete o foco em backend, sem desqualificar o projeto.

**Instalação e operação:** preparar core ESP32/bibliotecas, `secrets.h` e dados solares; compilar para `esp32:esp32:d1_uno32`, conforme o [guia](https://github.com/anvmano/LightingController/blob/main/README.md). Upload e validação exigem hardware compatível.

**Limitações e melhorias:** TLS sem validação de certificado; horários em RAM, sem expiração por data após uma leitura válida; agenda dependente do minuto; chamadas de rede bloqueantes. Testar transições, falha de rede e virada de data. Sem fotos, esquema completo ou demonstração física versionada identificados.

**Competências e diferencial:** controle de atuadores, interpolação de brilho, agenda temporal e integração REST de um dispositivo de finalidade específica.

**Evidências:** [sketch](https://github.com/anvmano/LightingController/blob/26fff2f1972567e9cf4dec678ce463311d51cfeb/LightingController.ino) · [dados solares](https://github.com/anvmano/LightingController/blob/26fff2f1972567e9cf4dec678ce463311d51cfeb/03_WeatherAndSun.ino) · [brilho e relé](https://github.com/anvmano/LightingController/blob/26fff2f1972567e9cf4dec678ce463311d51cfeb/04_Actuators.ino) · [agenda](https://github.com/anvmano/LightingController/blob/26fff2f1972567e9cf4dec678ce463311d51cfeb/05_Tasks.ino)

## Relação entre os projetos de clima

Os códigos compartilham caminhos e campos do Firebase: a estação produz temperatura/umidade e eventos solares; SensorsController produz dados do ar e aquário; LightingController consome eventos solares. Os dashboards web e .NET leem esses grupos de dados.

Essa compatibilidade mostra uma relação técnica. Não comprova que todos estejam conectados à mesma instalação ativa nem que a migração .NET tenha paridade completa validada nesta auditoria.

[Voltar à apresentação](README.md)
