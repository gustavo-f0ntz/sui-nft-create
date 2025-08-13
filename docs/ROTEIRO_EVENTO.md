# 🎨 NFT na Sui - Guia Rápido para o Evento

## 🏃‍♂️ ROTEIRO DE APRESENTAÇÃO (45-60 minutos)

---

## 📊 SLIDE 1: Introdução (5 min)
### "NFT? Blockchain? Move? Vamos descomplicar!"

**Para iniciantes:**
- 🖼️ **NFT** = Certificado digital único (como selo de autenticidade)
- ⛓️ **Blockchain** = Livro de registros que ninguém pode falsificar
- 🏎️ **Sui** = Blockchain moderna e rápida
- 🔧 **Move** = Linguagem para criar contratos inteligentes

**Analogia simples:** 
> "É como criar um certificado de autenticidade digital para uma obra de arte que fica guardado em um cofre público que todo mundo pode ver, mas ninguém pode falsificar."

---

## 📊 SLIDE 2: Estrutura do Projeto (5 min)
### "Como organizamos nosso código"

```
meu_nft_exemplo/
├── Move.toml          ← "Identidade do projeto"
├── sources/           ← "Nosso código principal"
│   └── meu_nft_exemplo.move
├── tests/            ← "Testes"
└── build/            ← "Arquivos compilados"
```

**Explicação:**
- **Move.toml** = Como um "documento de identidade" do projeto
- **sources/** = Onde escrevemos o código que cria os NFTs
- **build/** = O computador gera isso automaticamente

---

## 📊 SLIDE 3: Anatomia do NFT (10 min)
### "O que tem dentro de um NFT?"

```move
public struct MeuNFT has key, store {
    id: UID,           ← "RG do NFT" (único)
    name: String,      ← "Nome" (ex: "Arte Digital #1")
    description: String, ← "Descrição" (ex: "Minha primeira arte")
    url: String        ← "Link da imagem"
}
```

**Características importantes:**
- **`has key`** = Pode ter dono (como uma casa)
- **`has store`** = Pode ser guardado (como em uma coleção)
- **`UID`** = Identidade única (como impressão digital)

---

## 📊 SLIDE 4: Código Principal - Parte 1 (10 min)
### "Configurando as ferramentas"

```move
module meu_nft_exemplo::meu_nft {
    // Importando ferramentas
    use sui::display;           ← Para mostrar NFT bonito
    use std::string::String;    ← Para trabalhar com texto
    use sui::package::Publisher; ← Para provar autoria
```

**Analogia das ferramentas:**
- `display` = Vitrine da loja (como o NFT aparece)
- `string` = Ferramenta para escrever/ler texto
- `package` = Cartório (prova que você é o criador)

---

## 📊 SLIDE 5: Código Principal - Parte 2 (10 min)
### "Criando NFTs - A função mint()"

```move
entry fun mint(
    name: vector<u8>,        ← Nome em formato de bytes
    description: vector<u8>, ← Descrição em bytes
    url: vector<u8>,         ← URL da imagem em bytes
    ctx: &mut TxContext      ← Informações da transação
) {
    // 1. Criar o NFT
    let nft = MeuNFT {
        id: object::new(ctx),              ← Gera ID único
        name: string::utf8(name),          ← Converte para texto
        description: string::utf8(description),
        url: string::utf8(url),
    };
    
    // 2. Enviar para quem chamou a função
    transfer::public_transfer(nft, tx_context::sender(ctx));
}
```

**Processo simplificado:**
1. 📝 Recebe as informações
2. 🏗️ Monta o NFT
3. 📤 Envia para sua carteira

---

## 📊 SLIDE 6: Display - A "Vitrine" (5 min)
### "Como seu NFT aparece nas carteiras"

```move
entry fun create_display(publisher: &Publisher, ctx: &mut TxContext) {
    let mut display = display::new_with_fields<MeuNFT>(
        publisher,
        // O QUE mostrar
        vector[b"name", b"description", b"image_url"],
        // DE ONDE vem cada info
        vector[b"{name}", b"{description}", b"{url}"],
        ctx
    );
}
```

**Como funciona:**
- Define **quais campos** mostrar (`name`, `description`, `image_url`)
- Define **de onde** vem cada informação (`{name}`, `{description}`, `{url}`)
- É como criar um "template" de como exibir o NFT

---

## 📊 SLIDE 7: Hands-On - Parte 1 (10 min)
### "Vamos colocar a mão na massa!"

### PASSO 1: Compilar
```bash
sui move build
```
**O que acontece:** Transforma nosso código em algo que a blockchain entende

### PASSO 2: Publicar
```bash
sui client publish --gas-budget 100000000
```
**O que acontece:** Coloca nosso "molde de NFT" na blockchain

### PASSO 3: Criar Display
```bash
sui client call --function create_display --module meu_nft \
  --package [PACKAGE_ID] --args [PUBLISHER_ID] --gas-budget 10000000
```
**O que acontece:** Cria a "vitrine" para nossos NFTs

---

## 📊 SLIDE 8: Hands-On - Parte 2 (10 min)
### "Criando seu primeiro NFT!"

### PASSO 4: Mintar NFT
```bash
sui client call --function mint --module meu_nft \
  --package [PACKAGE_ID] \
  --args "Meu Primeiro NFT" "Criado no workshop de hoje!" "https://exemplo.com/imagem.png" \
  --gas-budget 10000000
```

### EXEMPLOS PRÁTICOS:
```bash
# NFT de Arte Digital
--args "Pôr do Sol Digital" "Arte criada com IA" "https://minha-arte.com/por-do-sol.png"

# NFT de Meme
--args "Gato Programador" "Meme sobre desenvolvedores" "https://meus-memes.com/gato.jpg"

# NFT de Música
--args "Batida Lofi #1" "Música relaxante para codar" "https://minha-musica.com/cover.png"
```

---

## 📊 SLIDE 9: Conceitos Importantes (5 min)
### "Coisas que você precisa saber"

### 🔐 **Segurança**
- **One-Time Witness** = Só funciona uma vez (prova de originalidade)
- **Publisher** = Só o criador pode modificar o Display
- **UID** = Cada NFT tem ID único e imutável

### 💰 **Gas/Combustível**
- Toda operação na blockchain custa "gas"
- É como combustível do carro
- Valores maiores = transação mais rápida

### 🔄 **Transferência**
- NFTs podem ser enviados para outras carteiras
- A propriedade fica registrada na blockchain
- Impossível de falsificar ou duplicar

---

## 📊 SLIDE 10: Desafio Final (10 min)
### "Seu turno de criar!"

### 🎯 **DESAFIO:**
Crie um NFT com tema **"Minha Primeira Experiência com Blockchain"**

### 📝 **REQUISITOS:**
1. **Nome criativo** relacionado ao tema
2. **Descrição pessoal** (como foi a experiência)
3. **Imagem** (pode usar qualquer URL pública)

### 🚀 **BÔNUS:** 
- Modifique o código para adicionar um campo `creator`
- Adicione um campo `date_created`
- Personalize as mensagens de display

### 💡 **DICA:**
Use este template:
```
Nome: "Minha Jornada Blockchain - [Seu Nome]"
Descrição: "Hoje aprendi a criar NFTs e foi [sua impressão]!"
URL: "https://via.placeholder.com/400x400/0099ff/ffffff?text=Meu+NFT"
```

---

## 📊 SLIDE 11: Próximos Passos (5 min)
### "Para onde ir agora?"

### 🔧 **Melhorias Possíveis:**
- Adicionar campos de raridade
- Criar sistema de royalties
- Implementar coleções
- Adicionar metadata mais complexa

### 🌐 **Conectar com Interfaces:**
- Criar frontend web
- Conectar com carteiras
- Marketplace próprio

### 📚 **Recursos para Estudar:**
- [Documentação Sui](https://docs.sui.io/)
- [Move Language](https://move-language.github.io/)
- [Exemplos de Código](https://github.com/MystenLabs/sui/tree/main/examples)

---

## 📊 SLIDE 12: Q&A e Conclusão (10 min)
### "Perguntas e Reflexões"

### ✅ **O que aprendemos hoje:**
- Como funciona um NFT por dentro
- Como programar em Move (linguagem da Sui)
- Como publicar na blockchain
- Como criar e transferir NFTs

### 🤔 **Perguntas Comuns:**
- **"Posso ganhar dinheiro com isso?"** - Sim, criando NFTs valiosos ou serviços
- **"É difícil aprender?"** - Com prática, fica mais fácil
- **"Preciso ser programador?"** - Ajuda, mas existem ferramentas visuais
- **"É caro publicar?"** - Depende da rede, Sui é bem barata

### 🎯 **Desafio para Casa:**
Crie uma coleção de 5 NFTs com tema próprio!

---

## 🎉 **PARABÉNS!**
### Vocês agora são criadores de NFTs na blockchain Sui! 

**Continue explorando, criando e aprendendo! 🚀**
