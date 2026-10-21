# Catálogo de projetos

[Apresentação](README.md) · [Experiência e formação](docs/EXPERIENCIA.md)

Projetos de backend C#/.NET, bancos de dados, visualização e integração com dispositivos. Cada seção apresenta a solução, as tecnologias e os pontos de implementação que podem ser consultados no código.

## Navegação por área

- **Backend e APIs .NET:** [Estação Climática em C#](#estacao-climatica-csharp).
- **Bancos de dados:** [Oracle Database](#oracle-database).
- **Sistemas web:** [Dashboard climático](#anvmano-github-io).
- **Eletrônica e integrações:** [Estação ESP32](#estacao-climatica) e [SensorsController](#sensorscontroller).
- **Automação:** [LightingController](#lightingcontroller).

## estacao-climatica-csharp

**API e dashboard de monitoramento climático em C#/.NET.**

Evolução do dashboard estático para uma aplicação com processamento no backend, consultas de históricos e visualização de dados de ambientes e aquário.

**Tecnologias:** C#, .NET 8, ASP.NET Core, Firebase REST, JavaScript e Chart.js. Testes com xUnit e Playwright.

- API para consultar medições, séries temporais, estatísticas, comparações, alertas e exportações.
- Modo público com consulta por CEP, cidade ou localização e previsão de 15 dias.
- Acesso interno por Firebase ID token e lista de e-mails autorizados; assistente com cálculos locais e integração Gemini opcional.

**Diferencial técnico:** separação em Domain, Application, Infrastructure e Web, com injeção de dependências, acesso HTTP isolado, cache e novas tentativas de leitura do Firebase.

[Código](https://github.com/anvmano/estacao-climatica-csharp) · [Instalação e execução](https://github.com/anvmano/estacao-climatica-csharp/blob/main/docs/README.md) · [Organização do backend](https://github.com/anvmano/estacao-climatica-csharp/tree/2dd5fe9a43c697f680ad8463a67d4ffb4bd8f52a/src) · [Testes](https://github.com/anvmano/estacao-climatica-csharp/tree/2dd5fe9a43c697f680ad8463a67d4ffb4bd8f52a/tests/EstacaoClimatica.Tests)

## Oracle-Database

**Guias e biblioteca de scripts para administração Oracle.**

Acervo técnico ligado à minha experiência como DBA, organizado para localizar procedimentos por tarefa ou sintoma.

**Tecnologias:** Oracle Database, SQL, PL/SQL, SQL*Plus, RMAN, Oracle Linux e OCI; Python nos verificadores locais.

- Biblioteca com 77 consultas de diagnóstico, 7 intervenções e 6 geradores de DDL, além do inicializador de sessão.
- Guias de instalação, backup, recuperação, desempenho e administração, com roteiros de solução de problemas.
- Scripts de manutenção com parâmetros e verificações de banco, container e alvo; geração de DDL para revisão.

**Diferencial técnico:** separação entre diagnóstico, intervenção e geração de comandos, com instruções de contexto e escopo para cada tarefa.

[Código e documentação](https://github.com/anvmano/Oracle-Database) · [Catálogo SQL](https://github.com/anvmano/Oracle-Database/blob/main/scripts/CATALOGO.md) · [Exemplo de manutenção](https://github.com/anvmano/Oracle-Database/blob/93d72004e68216b00bc67afe6e2c977b3a701f6a/scripts/manutencao/recompilar_objeto.sql) · [Verificadores](https://github.com/anvmano/Oracle-Database/tree/93d72004e68216b00bc67afe6e2c977b3a701f6a/tests)

## anvmano-github-io

**Dashboard web para dados climáticos e de aquário.**

Aplicação estática para explorar medições, acompanhar condições dos ambientes e consultar clima público no navegador.

**Tecnologias:** JavaScript, HTML, CSS, Chart.js, Firebase, html2canvas e jsPDF. Integrações com BrasilAPI, ViaCEP e Open-Meteo.

- Gráficos sincronizados, zoom, tabelas, estatísticas, heatmaps e indicadores de qualidade das leituras.
- Exportação de relatórios PDF/JSON e visualização de eventos solares.
- Consulta pública por CEP, cidade ou localização; login Google para acesso ao fluxo interno.

**Diferencial técnico:** módulos por responsabilidade, carregamento de recursos sob demanda e cenários de interface e acessibilidade com Playwright Core e axe.

[Código](https://github.com/anvmano/anvmano.github.io) · [Demonstração](https://anvmano.github.io/) · [Execução e documentação](https://github.com/anvmano/anvmano.github.io/blob/main/docs/README.md) · [Implementação das consultas públicas](https://github.com/anvmano/anvmano.github.io/blob/c4d5b5e624f0f5fe7c82742e788f3ddcde0da4e0/scripts/external/external-weather-service.js)

## estacao-climatica

**Estação ESP32 com sensores, histórico e consultas pelo Telegram.**

Firmware que coleta temperatura e umidade, mantém o relógio da estação e disponibiliza dados para outros componentes do sistema climático.

**Tecnologias:** C++/Arduino, ESP32, DHT22, DS3231, Firebase ESP32 Client, Telegram, NTP e LittleFS. Integrações com OpenWeather, Sunrise-Sunset e Nominatim.

- Leitura de temperatura, umidade e sensação térmica, histórico climático e eventos solares.
- Comandos Telegram para consultas da estação e por CEP/localização, com distinção de remetentes autorizados e visitantes.
- Fila local para novas tentativas de gravação no Firebase.

**Diferencial técnico:** integração de sensor, relógio, bot e armazenamento, com destinos de gravação determinísticos nas novas tentativas de envio.

[Código e instalação](https://github.com/anvmano/estacao-climatica) · [Integração Firebase](https://github.com/anvmano/estacao-climatica/blob/cc28a94828c8837fd1f625945856872f0f046324/05_Firebase.ino) · [Persistência local](https://github.com/anvmano/estacao-climatica/blob/cc28a94828c8837fd1f625945856872f0f046324/08_FirebaseQueue.ino)

## SensorsController

**Aquisição de dados do ar e da água de aquário com ESP32.**

Firmware que reúne leituras de múltiplos sensores e envia históricos ao Firebase, com sinalização de disponibilidade por sensor.

**Tecnologias:** C++/Arduino, ESP32/WEMOS D1 R32, BME680, MQ135, DS18B20, ArduinoJson, Firebase REST e LittleFS.

- Temperatura, umidade e pressão do ar; estimativas de gases dependentes da calibração do MQ135.
- Temperatura da água, TDS, turbidez e pH, com compensação de temperatura e filtragem por mediana nas leituras aplicáveis.
- Diagnóstico inicial, registros por categoria e fila local com novas tentativas de envio por HTTP PUT.

**Diferencial técnico:** processamento das leituras antes da montagem do JSON, estados de cada sensor e separação entre aquisição e controle de iluminação. As calibrações precisam corresponder à montagem física.

[Código e instalação](https://github.com/anvmano/SensorsController) · [Leituras do aquário](https://github.com/anvmano/SensorsController/blob/f6840dbf34d2e15f90c4a4ff4429f6863aa5cdd5/04_AquariumSensors.ino) · [Fila de envio](https://github.com/anvmano/SensorsController/blob/f6840dbf34d2e15f90c4a4ff4429f6863aa5cdd5/07_FirebaseQueue.ino)

## LightingController

**Controle de iluminação de aquário a partir do ciclo solar.**

Firmware de automação que ajusta cores e brilho ao longo do dia e aciona uma luz branca na janela do zênite.

**Tecnologias:** C++/Arduino, ESP32/WEMOS D1 R32, FastLED, NeoPixel, ArduinoJson, NTP e Firebase REST.

- Controle de 125 LEDs em cinco fileiras e acionamento de relé.
- Transições de brilho por interpolação smoothstep e horários solares consultados no Firebase.
- Inicialização com LEDs e relé desligados até obter horário e primeira leitura solar válidos.

**Diferencial técnico:** aplicação de uma curva de iluminação temporal ao controle de atuadores, separada do firmware de sensores.

[Código e instalação](https://github.com/anvmano/LightingController) · [Curva de brilho e relé](https://github.com/anvmano/LightingController/blob/26fff2f1972567e9cf4dec678ce463311d51cfeb/04_Actuators.ino) · [Consulta dos horários solares](https://github.com/anvmano/LightingController/blob/26fff2f1972567e9cf4dec678ce463311d51cfeb/03_WeatherAndSun.ino)

## Como os projetos de clima se relacionam

A estação ESP32 produz dados climáticos e solares; o SensorsController coleta dados do ar e aquário; o LightingController consome os horários solares. Os dashboards web e .NET usam os mesmos grupos de dados do Firebase para consulta e visualização.

Para executar cada projeto, consulte os requisitos, a configuração e as limitações descritas em sua documentação.

[Voltar à apresentação](README.md)
