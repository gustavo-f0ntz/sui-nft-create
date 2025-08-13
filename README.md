# 🎨 Workshop NFT na Blockchain Sui

## 🎯 Descrição
Projeto educacional completo para ensinar criação de NFTs na blockchain Sui utilizando a linguagem Move. Material desenvolvido para workshops e eventos de blockchain.

## 🚀 O que você vai aprender
- Como criar NFTs do zero na blockchain Sui
- Linguagem de programação Move
- Conceitos de blockchain e contratos inteligentes
- Como publicar e interagir com contratos na rede

## 📁 Estrutura do Projeto

```
meu_nft_exemplo/
├── sources/                    # Código-fonte Move
│   └── meu_nft_exemplo.move   # Contrato principal do NFT
├── tests/                     # Testes do contrato
├── docs/                      # 📚 Material educacional completo
│   ├── GUIA_COMPLETO_NFT.md   # Guia detalhado linha por linha
│   ├── ROTEIRO_EVENTO.md      # Apresentação estruturada (60 min)
│   ├── COLA_DO_APRESENTADOR.md # Manual completo para apresentador
│   ├── COMANDOS_PRATICOS.md   # Comandos e troubleshooting
│   ├── EXERCICIOS_PRATICOS.md # Atividades hands-on
│   ├── BRIEFING_15MIN.md      # Briefing rápido
│   ├── CHEAT_SHEET.md         # Cola de bolso
│   ├── COMANDOS_PRONTOS.md    # Comandos copy-paste
│   ├── PLANO_EMERGENCIA.md    # Para eventos last-minute
│   └── RESUMO_EXECUTIVO.md    # Visão geral completa
├── Move.toml                  # Configuração do projeto
└── README.md                  # Este arquivo
```

## 🎓 Para Educadores

### Material Pronto para Uso:
- **Apresentação completa** (45-60 minutos)
- **Explicações linha por linha** do código
- **Comandos prontos** para copy-paste
- **Troubleshooting** de problemas comuns
- **Exercícios práticos** para diferentes níveis

### Como Usar:
1. **Para workshop rápido:** Use `ROTEIRO_EVENTO.md`
2. **Para estudo aprofundado:** Use `GUIA_COMPLETO_NFT.md`
3. **Para emergência:** Use `CHEAT_SHEET.md` e `COMANDOS_PRONTOS.md`

## 🛠️ Como Executar

### Pré-requisitos:
- [Sui CLI](https://docs.sui.io/build/install) instalado
- Carteira configurada
- Tokens de teste (faucet)

### Comandos Básicos:
```bash
# 1. Compilar
sui move build

# 2. Publicar
sui client publish --gas-budget 100000000

# 3. Criar Display
sui client call --function create_display --module meu_nft --package [PACKAGE_ID] --args [PUBLISHER_ID] --gas-budget 10000000

# 4. Criar NFT
sui client call --function mint --module meu_nft --package [PACKAGE_ID] --args "Nome" "Descrição" "URL" --gas-budget 10000000
```

## 🎯 Público-Alvo
- **Iniciantes** em blockchain e programação
- **Desenvolvedores** querendo aprender Move/Sui
- **Educadores** de tecnologia
- **Entusiastas** de NFTs e Web3

## 📚 Recursos Adicionais
- [Documentação Sui](https://docs.sui.io/)
- [Move Language](https://move-language.github.io/)
- [Explorer Sui](https://suiexplorer.com/)

## 🤝 Contribuições
Contribuições são bem-vindas! Este material foi criado para ser compartilhado e melhorado pela comunidade.

## 📄 Licença
Este projeto é de código aberto e livre para uso educacional.

---

**🚀 Transforme conhecimento blockchain em experiência prática!**
