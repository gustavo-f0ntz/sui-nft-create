# 📋 COMANDOS PRONTOS - COPY & PASTE PARA AMANHÃ

## 🚨 INSTRUÇÕES PARA O APRESENTADOR

### **ANTES DO EVENTO:**
1. Compile: `sui move build`
2. Publique: `sui client publish --gas-budget 100000000`
3. **ANOTE OS IDs** que aparecerem
4. **SUBSTITUA** nos comandos abaixo

---

## 🔥 COMANDOS PRONTOS (substituir [PACKAGE_ID] e [PUBLISHER_ID])

### **COMANDO 1: Criar Display**
```bash
sui client call --function create_display --module meu_nft --package [PACKAGE_ID] --args [PUBLISHER_ID] --gas-budget 10000000
```

### **COMANDO 2: NFT de Exemplo**
```bash
sui client call --function mint --module meu_nft --package [PACKAGE_ID] --args "Workshop Sui NFT" "Meu primeiro NFT criado no evento!" "https://via.placeholder.com/400x400/0099ff/ffffff?text=Workshop+NFT" --gas-budget 10000000
```

### **COMANDO 3: NFT Personalizado 1**
```bash
sui client call --function mint --module meu_nft --package [PACKAGE_ID] --args "Arte Digital Brasileira" "Criado com orgulho no Brasil" "https://via.placeholder.com/400x400/00ff00/ffffff?text=Brasil+NFT" --gas-budget 10000000
```

### **COMANDO 4: NFT Personalizado 2**
```bash
sui client call --function mint --module meu_nft --package [PACKAGE_ID] --args "Blockchain Revolution" "O futuro chegou!" "https://via.placeholder.com/400x400/ff6b6b/ffffff?text=Future+NFT" --gas-budget 10000000
```

---

## 🎨 TEMAS PRONTOS PARA CRIAR NO EVENTO

### **Copy-paste prontos (só trocar [PACKAGE_ID]):**

#### **Tema: Animais**
```bash
sui client call --function mint --module meu_nft --package [PACKAGE_ID] --args "Gato Cósmico" "Um felino viajante do espaço" "https://via.placeholder.com/400x400/9b59b6/ffffff?text=Gato+Espacial" --gas-budget 10000000
```

#### **Tema: Comida**
```bash
sui client call --function mint --module meu_nft --package [PACKAGE_ID] --args "Pizza Suprema" "A pizza mais épica do universo" "https://via.placeholder.com/400x400/e74c3c/ffffff?text=Pizza+NFT" --gas-budget 10000000
```

#### **Tema: Tecnologia**
```bash
sui client call --function mint --module meu_nft --package [PACKAGE_ID] --args "IA do Futuro" "Inteligência artificial em NFT" "https://via.placeholder.com/400x400/3498db/ffffff?text=AI+NFT" --gas-budget 10000000
```

#### **Tema: Natureza**
```bash
sui client call --function mint --module meu_nft --package [PACKAGE_ID] --args "Floresta Mágica" "A natureza em forma digital" "https://via.placeholder.com/400x400/27ae60/ffffff?text=Nature+NFT" --gas-budget 10000000
```

#### **Tema: Esporte**
```bash
sui client call --function mint --module meu_nft --package [PACKAGE_ID] --args "Gol Histórico" "O gol que mudou tudo" "https://via.placeholder.com/400x400/f39c12/ffffff?text=Goal+NFT" --gas-budget 10000000
```

---

## 🆘 COMANDOS DE EMERGÊNCIA

### **Se der erro de gas:**
```bash
sui client faucet
```

### **Ver objetos na carteira:**
```bash
sui client objects
```

### **Ver saldo:**
```bash
sui client balance
```

### **Ver detalhes de um NFT:**
```bash
sui client object [OBJECT_ID]
```

### **Recompilar (se algo der errado):**
```bash
sui move build --clean
```

---

## 🌐 LINKS IMPORTANTES (abrir em abas)

### **Explorer para mostrar NFTs:**
```
https://suiexplorer.com/
```

### **Faucet (tokens grátis):**
```
https://faucet.devnet.sui.io/
```

### **Documentação (backup):**
```
https://docs.sui.io/
```

---

## 🎬 FALAS PRONTAS PARA CADA COMANDO

### **Ao compilar:**
> *"Agora vamos traduzir nosso código para a linguagem que a blockchain entende."*

### **Ao publicar:**
> *"Estamos colocando nosso 'molde de NFT' na rede mundial. Isso vai gerar alguns números importantes que vou anotar."*

### **Ao criar display:**
> *"Agora vamos criar a 'vitrine' que vai mostrar nossos NFTs de forma bonita nas carteiras."*

### **Ao criar primeiro NFT:**
> *"E agora... o momento mágico! Vamos criar nosso primeiro NFT!"*

### **Ao mostrar no explorer:**
> *"Vejam só! Aqui está nosso NFT vivinho na blockchain. Ele agora existe para sempre!"*

---

## 📱 TEMPLATE DE APRESENTAÇÃO NO CELULAR

### **Para enviar para seu chefe:**

```
🚀 ROTEIRO RÁPIDO:

1️⃣ Falar: "NFT = certificado digital"
2️⃣ Compilar: sui move build  
3️⃣ Publicar: sui client publish...
4️⃣ Display: sui client call...
5️⃣ NFT: sui client call...
6️⃣ Mostrar no explorer
7️⃣ Criar mais NFTs com público

✅ Lembrar: "Vocês são criadores digitais agora!"
```

---

## 🎯 EXEMPLO DE SEQUÊNCIA COMPLETA

### **Para teste hoje à tarde:**

```bash
# 1. Preparar
cd /home/f0ntz/Documents/meu_nft_exemplo
sui move build

# 2. Publicar
sui client publish --gas-budget 100000000
# ANOTE: Package: 0xabc123... Publisher: 0xdef456...

# 3. Display  
sui client call --function create_display --module meu_nft --package 0xabc123... --args 0xdef456... --gas-budget 10000000

# 4. NFT
sui client call --function mint --module meu_nft --package 0xabc123... --args "Teste NFT" "Funcionou!" "https://via.placeholder.com/400x400/00ff00/ffffff?text=Success" --gas-budget 10000000

# 5. Ver resultado
sui client objects
```

---

## 🔥 DICA DE OURO

### **Se algo quebrar:**
1. **Mantenha a calma**
2. **Fale:** "Isso é normal em blockchain, vamos resolver"
3. **Use:** `sui client faucet` (primeira tentativa)
4. **Ou:** Mostre NFTs já criados no explorer
5. **Backup:** Foque nos conceitos e deixe prática para depois

---

## 💪 MENSAGEM FINAL

**Seu chefe tem TUDO que precisa aqui!** 

- ✅ Comandos prontos para copy-paste
- ✅ Falas preparadas
- ✅ Planos B e C
- ✅ Seu suporte online

**AMANHÃ VAI SER SUCESSO TOTAL! 🚀**
