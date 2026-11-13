# ACOUSTIC FORGE — Speaker Tycoon

Protótipo jogável de um tycoon de engenharia eletroacústica em HTML, CSS e JavaScript puro.

## Como executar

Os módulos JavaScript ES Modules precisam de um servidor HTTP local. Não abra `index.html` diretamente com `file://`.

1. Extraia a pasta `AcousticForge`.
2. Abra um terminal dentro dela.
3. Execute:

```bash
python -m http.server 8000
```

4. Abra `http://localhost:8000` no navegador.

No Windows, também é possível iniciar com duplo clique em `INICIAR.bat` (requer Python instalado e o comando `py` disponível).

Também é possível hospedar a pasta em qualquer serviço estático que sirva HTML, CSS e JavaScript.

## Sistemas implementados

- Escritório visual isométrico 2.5D com painel da empresa, upgrades, notícias e extrato semanal.
- Bancada de engenharia com seleção de diâmetro, carcaça, conjunto magnético, bobina, cone, calota, suspensão e caixa.
- Estimativas de Fs, Re, Bl, Qms, Qes, Qts, Vas, Xmax, sensibilidade, potência térmica, potência mecânica e potência segura.
- Curva de resposta em frequência e curva de impedância, com marcadores Fs, Fb e F3 e tooltip interativo.
- Corte transversal animado com telemetria de excursão e temperatura em função da potência e frequência selecionadas.
- Gerador de ruído rosa, varredura e batida via Web Audio API, com filtros HPF/LPF e EQ.
- Publicação de produtos inéditos, sucessores e versões Budget, com fãs por linha, classificador semântico local, extração de frequências em Hz/kHz e nota detalhada de cinco critérios.
- Vendas recorrentes, devoluções, garantias, royalties simplificados, fãs e reputação.
- Árvore de P&D, equipe, fornecedores, fidelidade e contratos corporativos.
- Salvamento automático via LocalStorage.

## Limites do modelo físico

Este é um simulador de jogo, não um substituto para um software de projeto eletroacústico ou medições de bancada. Os parâmetros derivam de equações de pequena-sinal e relações simplificadas entre componentes. A resistência e massa da bobina, o amortecimento, a excursão, a capacidade térmica, a resposta de cones e o alinhamento dutado usam estimativas e fatores de jogo. A resposta de caixas dutadas e a curva de impedância são aproximações visuais; o modelo ainda não resolve a rede eletromecânica completa, perdas do duto, vazamentos, indutância variável, não linearidades de Bl/Kms, compressão térmica transitória ou fluxo de ar.

O áudio de teste aplica os filtros DSP selecionados e um passa-altas aproximado relacionado ao F3 estimado. A saída é limitada em nível para reduzir o risco de volume excessivo, mas o usuário ainda deve começar com volume baixo.

## Controles

- Use a navegação lateral para alternar entre Escritório, Bancada, Produtos, P&D, Fornecedores e Contratos.
- Configure o falante na bancada. Os parâmetros e gráficos são recalculados automaticamente.
- Publique um produto na página Produtos. Especificações exageradas afetam vendas futuras, devoluções e reputação.
- Avance a semana para executar vendas, pesquisa, folha operacional e pós-venda.
- O botão de salvar grava a campanha no armazenamento local do navegador.

## Tecnologias

HTML5, CSS3, JavaScript ES Modules, Canvas 2D, Web Audio API e LocalStorage. Sem dependências de build ou pacotes externos. As fontes web usam Google Fonts, com fontes locais genéricas como fallback.


## Instalação como PWA no Android

1. Publique **todo o conteúdo desta pasta** em uma hospedagem HTTPS (por exemplo, GitHub Pages, Netlify ou Cloudflare Pages). O PWA não pode ser instalado corretamente abrindo `index.html` por `file://`.
2. No Android, abra o endereço publicado no Chrome.
3. Use **Instalar app** no cabeçalho quando aparecer, ou menu ⋮ → **Instalar app / Adicionar à tela inicial**.
4. Abra o ícone ACOUSTIC FORGE na tela inicial. O service worker guarda os arquivos principais para uso offline depois da primeira abertura online.

### O que o PWA adiciona
- Manifesto com nome, ícones, cores e modo standalone.
- Service worker com cache do shell do jogo e fallback offline.
- Fluxo de instalação do Chrome para Android.
- Barra de navegação inferior adaptada para celular e áreas seguras do Android.

### Limitações
A instalação exige HTTPS (ou localhost para testes). Recursos que dependem de fontes externas podem não estar disponíveis offline. O salvamento da campanha continua no armazenamento local do navegador/dispositivo; ele não sincroniza automaticamente entre aparelhos. Para publicar atualizações, altere a versão do cache em `sw.js`.
