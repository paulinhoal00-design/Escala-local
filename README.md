# Minha Escala Local

Versão independente com o mesmo calendário e funções da versão online, usando IndexedDB no próprio navegador. Não usa Firebase, login, SDK externo nem servidor de banco de dados.

## Publicar e instalar

1. Extraia o ZIP e publique todos os arquivos em um novo repositório, por exemplo Escala-Local, com GitHub Pages e HTTPS. Os ícones ficam na raiz junto do index.html.
2. Abra o endereço online uma vez e aguarde o carregamento completo para que o Service Worker armazene os arquivos.
3. Instale pelo convite do aplicativo ou pelo menu do Chrome. Após o primeiro carregamento completo, o calendário e as gravações funcionam sem internet.

Use uma URL/pasta diferente para manter as versões online e local instaladas separadamente. Esta versão tem nome, identidade, banco e cache próprios. Não abra pelo gerenciador de arquivos (file://): use HTTPS ou localhost.

## Trazer as escalas existentes

Na versão online, entre em Configurações > Exportar JSON. Na versão local, entre em Configurações > Importar JSON e selecione o mesmo backup. Não há migração automática nem leitura do Firebase.

A importação valida os registros antes de gravar e salva toda a mesclagem em uma única transação: IDs iguais são substituídos e os demais registros locais permanecem. Uma falha de gravação cancela toda a transação.

## Como os dados ficam salvos

Escalas, períodos, ocorrências, notas e preferências ficam no IndexedDB. A confirmação de salvamento ocorre após a transação ser concluída. Abas abertas do mesmo aplicativo recebem aviso de atualização local quando o navegador suporta BroadcastChannel.

Os dados permanecem ao fechar e reabrir o navegador, mas não são sincronizados entre celulares, perfis ou navegadores. Limpar os dados do site, usar modo anônimo ou o navegador remover armazenamento pode apagar o banco. Faça backup JSON periodicamente e antes de trocar de aparelho ou limpar dados. Atualizações normais dos arquivos e do cache não apagam o IndexedDB.

## Funcionalidades preservadas

Calendários mensal e anual; escalas 12x36, 6x2, 6x1 e sequências T/F; períodos de aplicação; referência para inverter dias; folgas extras e trabalho extra; notas; temas claro/escuro/automático; cores; backup JSON; instalação PWA.

Para trocar turno preservando os anteriores, crie outro modelo e um novo período. Alterar um modelo existente afeta todos os períodos vinculados a ele, como na versão original.
