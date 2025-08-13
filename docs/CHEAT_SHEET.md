# 📇 CHEAT SHEET - COLA RÁPIDA DO APRESENTADOR

## 🎯 3 CONCEITOS PRINCIPAIS
1. **NFT** = Certificado digital único (como RG da arte)
2. **Blockchain** = Livro de registros que ninguém falsifica  
3. **Smart Contract** = Molde para criar NFTs

## ⚡ 4 COMANDOS ESSENCIAIS
```bash
# 1. COMPILAR
sui move build

# 2. PUBLICAR (anotar PACKAGE_ID e PUBLISHER_ID!)
sui client publish --gas-budget 100000000

# 3. DISPLAY (usar IDs copiados)
sui client call --function create_display --module meu_nft --package [PACKAGE_ID] --args [PUBLISHER_ID] --gas-budget 10000000

# 4. CRIAR NFT
sui client call --function mint --module meu_nft --package [PACKAGE_ID] --args "Nome" "Descrição" "URL" --gas-budget 10000000
```

## 🗣️ FALAS MÁGICAS
- **Início:** "NFT é um certificado que prova que você é dono de algo digital"
- **Código:** "Estamos criando um molde que qualquer um pode usar"
- **Compilar:** "Traduzindo para linguagem da blockchain" 
- **Publicar:** "Colocando nosso molde na rede mundial"
- **Display:** "Criando vitrine para mostrar NFT bonito"
- **Mint:** "Fabricando nosso primeiro certificado digital!"

## 🚨 SOS - SE DER RUIM
- **Erro gas:** `sui client faucet`
- **Não acha package:** Republicar tudo
- **Travou:** "Vamos do último ponto que funcionou"
- **Perdeu:** `sui client objects` (mostra o que tem na carteira)

## 🎪 INTERAÇÃO COM PÚBLICO
- **Pergunta inicial:** "Quem já ouviu falar em NFT?"
- **Durante:** "Isso é magia ou tecnologia?" (risos)
- **Resultado:** "Parabéns! Vocês são criadores de NFT agora!"

## 📱 URLs IMPORTANTES
- **Explorer:** https://suiexplorer.com/ (mostrar NFTs criados)
- **Faucet:** https://faucet.devnet.sui.io/ (pedir tokens)

## 🎯 ESTRUTURA (60 min)
- **0-10min:** Conceitos + interação
- **10-25min:** Código linha por linha  
- **25-50min:** Hands-on (4 comandos)
- **50-60min:** Personalização + Q&A

## 💡 DICA DE OURO
**Se algo quebrar:** Mantenha a calma, fale "blockchain às vezes é temperamental, mas vamos resolver!" e siga para próximo passo.

---
**VOCÊ CONSEGUE! 🚀 É SÓ SEGUIR O ROTEIRO!**
