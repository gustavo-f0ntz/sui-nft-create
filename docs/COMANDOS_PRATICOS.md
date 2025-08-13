# 🛠️ Comandos Práticos e Troubleshooting - Evento NFT

## 🚀 Setup Inicial (Para Participantes)

### 1. Instalar Sui CLI
```bash
# Linux/macOS
curl -fLu/
sudo mv sui /usr/local/bin/

# Verificar instalação
sui --version
```

### 2. Configurar Carteira
```bash
# Criar nova carteira
sui client new-address ed25519

# Ver endereços disponíveis
sui client addresses

# Ver carteira ativa
sui client active-address

# Mudar carteira ativa
sui client switch --address [ENDEREÇO]
```

### 3. Conseguir Testnet Tokens
```bash
# Faucet para devnet
sui client faucet

# Verificar saldo
sui client balance
```

---

## 💼 Comandos do Workshop

### 📁 Preparação do Projeto
```bash
# Navegar para pasta do projeto
cd /home/f0ntz/Documents/meu_nft_exemplo

# Verificar arquivos
ls -la

# Ver conteúdo do Move.toml
cat Move.toml
```

### 🔨 Compilação e Deploy

#### Compilar
```bash
sui move build
```

**Se der erro:**
```bash
# Limpar cache e tentar novamente
sui move build --clean
```

#### Publicar na Devnet
```bash
sui client publish --gas-budget 100000000
```

**Saída esperada:**
```
Published Objects:
- Package ID: 0x[HASH_LONGO]
- Publisher Object: 0x[HASH_LONGO]
```

**⚠️ IMPORTANTE:** Copie e guarde o Package ID e Publisher Object!

### 🎨 Criando Display

```bash
sui client call \
  --function create_display \
  --module meu_nft \
  --package [PACKAGE_ID] \
  --args [PUBLISHER_OBJECT_ID] \
  --gas-budget 10000000
```

**Exemplo real:**
```bash
sui client call \
  --function create_display \
  --module meu_nft \
  --package 0x123abc... \
  --args 0x456def... \
  --gas-budget 10000000
```

### 🎯 Mintando NFTs

#### Template Básico
```bash
sui client call \
  --function mint \
  --module meu_nft \
  --package [PACKAGE_ID] \
  --args "Nome do NFT" "Descrição do NFT" "https://link-da-imagem.com" \
  --gas-budget 10000000
```

#### Exemplos Práticos

**NFT de Arte:**
```bash
sui client call \
  --function mint \
  --module meu_nft \
  --package [PACKAGE_ID] \
  --args "Pôr do Sol Digital" "Uma bela arte digital criada no workshop" "https://via.placeholder.com/400x400/ff6b6b/ffffff?text=Pôr+do+Sol" \
  --gas-budget 10000000
```

**NFT de Meme:**
```bash
sui client call \
  --function mint \
  --module meu_nft \
  --package [PACKAGE_ID] \
  --args "Gato Programador" "Meme clássico sobre desenvolvedores que trabalham de madrugada" "https://via.placeholder.com/400x400/4ecdc4/ffffff?text=Gato+Dev" \
  --gas-budget 10000000
```

**NFT Personalizado:**
```bash
sui client call \
  --function mint \
  --module meu_nft \
  --package [PACKAGE_ID] \
  --args "Minha Primeira Blockchain Experience" "Hoje aprendi a criar NFTs na Sui e foi incrível!" "https://via.placeholder.com/400x400/45b7d1/ffffff?text=First+NFT" \
  --gas-budget 10000000
```

---

## 🔍 Verificação e Debugging

### Ver Objetos da Carteira
```bash
# Ver todos os objetos
sui client objects

# Ver objetos de um tipo específico
sui client objects --filter package=[PACKAGE_ID]
```

### Ver Detalhes de um Objeto
```bash
sui client object [OBJECT_ID]
```

### Ver Transações
```bash
# Ver transações recentes
sui client transaction [TX_DIGEST]

# Ver histórico de transações
sui client transactions --count 10
```

### Explorer da Sui
```
https://suiexplorer.com/
```
- Cole o Object ID ou Transaction ID para ver detalhes

---

## 🚨 Troubleshooting Comum

### Erro: "Insufficient Gas"
```bash
# Solicitar mais tokens do faucet
sui client faucet

# Verificar saldo
sui client balance

# Tentar com mais gas
--gas-budget 20000000
```

### Erro: "Package not found"
**Causa:** Package ID incorreto
**Solução:** 
```bash
# Verificar último deploy
sui client transactions --count 5

# Ou recompilar e republicar
sui move build
sui client publish --gas-budget 100000000
```

### Erro: "Module not found"
**Causa:** Nome do módulo incorreto
**Verificação:**
```move
// No arquivo .move, verificar:
module meu_nft_exemplo::meu_nft {  // ← Nome correto
```

### Erro: "Publisher not found"
**Causa:** Publisher Object ID incorreto
**Solução:**
```bash
# Verificar objetos da carteira
sui client objects

# Procurar por objeto do tipo "Publisher"
```

### Erro: "Invalid UTF-8"
**Causa:** Caracteres especiais nos argumentos
**Solução:**
```bash
# Use apenas caracteres ASCII simples
# ✅ Correto: "Meu NFT"
# ❌ Incorreto: "Meu NFT com emojis 🚀"
```

---

## 📊 URLs de Imagem para Testes

### Placeholders Coloridos
```
# Azul
https://via.placeholder.com/400x400/0099ff/ffffff?text=Meu+NFT

# Vermelho
https://via.placeholder.com/400x400/ff6b6b/ffffff?text=Arte+Digital

# Verde
https://via.placeholder.com/400x400/51cf66/ffffff?text=Blockchain+NFT

# Roxo
https://via.placeholder.com/400x400/9775fa/ffffff?text=Workshop+Sui
```

### Imagens Públicas (Exemplo)
```
# Pixel Art
https://cdn.pixabay.com/photo/2021/11/12/03/04/pixel-art-6787124_960_720.png

# Abstract Art
https://cdn.pixabay.com/photo/2022/01/11/21/48/link-6931554_960_720.png
```

---

## 🎯 Checklist do Workshop

### ✅ Para o Apresentador
- [ ] Sui CLI instalado e funcionando
- [ ] Carteira configurada com tokens
- [ ] Projeto compilado
- [ ] Package publicado
- [ ] Display criado
- [ ] NFT de exemplo mintado
- [ ] URLs de teste preparadas

### ✅ Para os Participantes
- [ ] Sui CLI instalado
- [ ] Carteira criada
- [ ] Tokens do faucet recebidos
- [ ] Projeto baixado/clonado
- [ ] Comandos testados

---

## 📋 Template de Comandos para Copy-Paste

### Sequência Completa (Substitua [PACKAGE_ID] e [PUBLISHER_ID])
```bash
# 1. Compilar
sui move build

# 2. Publicar
sui client publish --gas-budget 100000000

# 3. Criar Display (COPIE OS IDs DO PASSO 2)
sui client call --function create_display --module meu_nft --package [PACKAGE_ID] --args [PUBLISHER_ID] --gas-budget 10000000

# 4. Mintar NFT
sui client call --function mint --module meu_nft --package [PACKAGE_ID] --args "Meu Primeiro NFT" "Criado no workshop Sui!" "https://via.placeholder.com/400x400/0099ff/ffffff?text=Workshop+NFT" --gas-budget 10000000

# 5. Ver resultado
sui client objects
```

---

## 🔧 Configurações Avançadas

### Mudar Rede (se necessário)
```bash
# Ver redes disponíveis
sui client envs

# Mudar para devnet
sui client switch --env devnet

# Mudar para testnet
sui client switch --env testnet
```

### Gas Optimization
```bash
# Para operações simples: 10000000
# Para publicação: 100000000
# Para operações complexas: 200000000
```

### Backup da Carteira
```bash
# Ver chaves privadas (CUIDADO!)
sui keytool list

# Exportar carteira
sui keytool export [ENDEREÇO] --key-identity [KEY_ID]
```

---

## 📞 Suporte Durante o Evento

### Links Úteis
- **Documentação Sui:** https://docs.sui.io/
- **Explorer:** https://suiexplorer.com/
- **Faucet:** https://faucet.devnet.sui.io/
- **Discord Sui:** https://discord.gg/sui

### Comandos de Emergência
```bash
# Resetar tudo
rm -rf ~/.sui
sui client

# Ver logs detalhados
sui client publish --gas-budget 100000000 --verbose

# Verificar conectividade
sui client active-env
```

---

**🎉 Boa sorte no workshop! Lembre-se: blockchain é sobre experimentação e aprendizado!**
