# Segurança e confiabilidade observadas

[Auditoria](AUDITORIA.md) · [Catálogo](../CATALOGO.md)

Registro separado da apresentação profissional. Achados de leitura dos snapshots listados na auditoria; não houve teste de invasão, consulta aos dados privados, uso de credenciais, alteração dos projetos ou verificação de regras remotas.

## Conexões dos firmwares

**Confirmado no código:** `setInsecure()` em `LightingController/03_WeatherAndSun.ino`, `SensorsController/07_FirebaseQueue.ino` e no cliente HTTPS de `estacao-climatica/02_Connectivity.ino`. Essa configuração deixa de verificar o certificado do servidor e permite que uma conexão interceptada seja aceita. O cliente Telegram da estação configura certificado raiz separadamente.

**Ação recomendada para trabalho futuro:** configurar validação de certificado com a cadeia adequada à plataforma, preservando sincronização de horário e tratamento de falhas. Rever logs, distribuição de binários e o transporte dos tokens Firebase na URL. Nenhum token ou valor de credencial foi reproduzido neste portfólio.

Fontes: [LightingController](https://github.com/anvmano/LightingController/blob/26fff2f1972567e9cf4dec678ce463311d51cfeb/03_WeatherAndSun.ino) · [SensorsController](https://github.com/anvmano/SensorsController/blob/f6840dbf34d2e15f90c4a4ff4429f6863aa5cdd5/07_FirebaseQueue.ino) · [conectividade da estação](https://github.com/anvmano/estacao-climatica/blob/cc28a94828c8837fd1f625945856872f0f046324/02_Connectivity.ino)

## Recuperação da fila de sensores

**Confirmado em `SensorsController/07_FirebaseQueue.ino`:** a recuperação no boot verifica formato do temporário, mas não comprova que a cópia esteja completa. Em seguida remove o principal antes de promover o temporário. Uma falha na renomeação pode deixar a fila indisponível depois da remoção. `copiarFila()` também não distingue principal ausente de falha ao abri-lo para leitura.

**Consequência:** persistência e repetição de `PUT` estão implementadas, mas não sustentam uma garantia geral de ausência de perdas em falhas de armazenamento ou energia.

**Ação recomendada:** revisar o protocolo de substituição/recuperação e testar os pontos de interrupção com falhas simuladas e hardware. O README original já documenta esses limites; o portfólio os preserva.

## Autorização e acesso Firebase

**Projeto web:** a lista de e-mails no frontend decide quais telas carregar; dados acessíveis pelo SDK precisam de regras de autorização no Realtime Database. App Check tem inicialização condicionada à configuração. Não foi examinado o enforcement no serviço remoto.

**Projeto .NET:** `Program.cs` verifica Firebase ID token e lista de e-mails nas rotas internas, com exceções para health e clima público. O cliente `FonteDadosFirebase` monta URLs de leitura sem anexar credencial de banco nem propagar o token recebido na API. Portanto, proteger a API não demonstra que o banco esteja protegido contra acesso direto, nem que o backend funcione com regras privadas sem configuração/implementação adicional.

**Ação recomendada:** definir uma estratégia de acesso do backend compatível com regras privadas e validar separadamente permissões de leitura/escrita. Não abrir o banco para contornar erros. As opções App Check da versão .NET não têm validação implementada; habilitar uma flag não cria essa proteção.

Fontes: [serviço Firebase web](https://github.com/anvmano/anvmano.github.io/blob/c4d5b5e624f0f5fe7c82742e788f3ddcde0da4e0/scripts/firebase-service.js) · [proteção da API](https://github.com/anvmano/estacao-climatica-csharp/blob/2dd5fe9a43c697f680ad8463a67d4ffb4bd8f52a/src/EstacaoClimatica.Web/Program.cs) · [leitura Firebase .NET](https://github.com/anvmano/estacao-climatica-csharp/blob/2dd5fe9a43c697f680ad8463a67d4ffb4bd8f52a/src/EstacaoClimatica.Infrastructure/Firebase/FirebaseDataSource.cs)

## Dados pessoais e confidenciais

O portfólio publica apenas nome, canais profissionais fornecidos, formação e resumo de experiência. O telefone e a localização do currículo, o próprio PDF, listas de outros usuários, identificadores de instalações e valores de configuração dos serviços não foram copiados.

Os três firmwares distribuem `secrets.example.h` e ignoram a configuração real. Nas cópias analisadas não foi encontrado `secrets.h` versionado. Configuração web Firebase é visível ao navegador por natureza e não foi tratada como prova de vazamento de chave privada. Não houve varredura de todo o histórico ou confirmação de validade de possíveis credenciais antigas.

Esses achados não alteram o comportamento dos projetos. Qualquer correção nos repositórios originais depende de autorização específica.
