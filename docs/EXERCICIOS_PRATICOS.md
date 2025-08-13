# 🎨 Exercícios e Modificações Práticas - Workshop NFT

## 🎯 Níveis de Dificuldade

### 🟢 INICIANTE: Personalizações Simples
### 🟡 INTERMEDIÁRIO: Novas Funcionalidades  
### 🔴 AVANÇADO: Recursos Complexos

---

## 🟢 EXERCÍCIOS INICIANTES

### 1. 📝 Mudando Textos e Nomes

#### Exercício: Personalize as mensagens
```move
// ANTES (linha ~4):
/// Módulo para criar um NFT de exemplo com Display Padrão.
module meu_nft_exemplo::meu_nft {

// DEPOIS - Personalize:
/// Meu módulo incrível para criar NFTs únicos!
module meu_nft_exemplo::meu_nft {
```

#### Exercício: Mude o nome da struct
```move
// ANTES:
public struct MeuNFT has key, store {

// DEPOIS:
public struct ArtePessoal has key, store {
// LEMBRE: Precisa mudar em TODO o código onde aparece MeuNFT!
```

### 2. 🎨 URLs de Teste Personalizadas

#### Crie NFTs com diferentes temas:
```bash
# NFT de Pet
sui client call --function mint --module meu_nft --package [PACKAGE_ID] \
--args "Meu Gato Max" "O gato mais fofo do mundo" "https://via.placeholder.com/400x400/ff9f43/ffffff?text=Gato+Max" \
--gas-budget 10000000

# NFT de Comida
sui client call --function mint --module meu_nft --package [PACKAGE_ID] \
--args "Pizza Margherita" "A melhor pizza do universo" "https://via.placeholder.com/400x400/ff6b6b/ffffff?text=Pizza" \
--gas-budget 10000000

# NFT de Lugar
sui client call --function mint --module meu_nft --package [PACKAGE_ID] \
--args "Praia do Futuro" "Meu lugar favorito para relaxar" "https://via.placeholder.com/400x400/74b9ff/ffffff?text=Praia" \
--gas-budget 10000000
```

---

## 🟡 EXERCÍCIOS INTERMEDIÁRIOS

### 3. ➕ Adicionando Novo Campo: Creator

#### Passo 1: Modificar a struct
```move
public struct MeuNFT has key, store {
    id: UID,
    name: String,
    description: String,
    url: String,
    creator: String,  // NOVO CAMPO!
}
```

#### Passo 2: Atualizar função mint
```move
entry fun mint(
    name: vector<u8>,
    description: vector<u8>,
    url: vector<u8>,
    creator: vector<u8>,  // NOVO PARÂMETRO!
    ctx: &mut TxContext
) {
    let nft = MeuNFT {
        id: object::new(ctx),
        name: string::utf8(name),
        description: string::utf8(description),
        url: string::utf8(url),
        creator: string::utf8(creator),  // NOVO CAMPO!
    };
    transfer::public_transfer(nft, tx_context::sender(ctx));
}
```

#### Passo 3: Atualizar o display
```move
let mut display = display::new_with_fields<MeuNFT>(
    publisher,
    vector[
        string::utf8(b"name"),
        string::utf8(b"description"),
        string::utf8(b"image_url"),
        string::utf8(b"creator")  // NOVO CAMPO NO DISPLAY!
    ],
    vector[
        string::utf8(b"{name}"),
        string::utf8(b"{description}"),
        string::utf8(b"{url}"),
        string::utf8(b"{creator}")  // NOVO VALOR!
    ],
    ctx
);
```

#### Passo 4: Teste o novo campo
```bash
sui client call --function mint --module meu_nft --package [PACKAGE_ID] \
--args "Arte Digital #1" "Minha primeira obra" "https://exemplo.com/arte.png" "João Silva" \
--gas-budget 10000000
```

### 4. 🌟 Adicionando Campo de Raridade

```move
public struct MeuNFT has key, store {
    id: UID,
    name: String,
    description: String,
    url: String,
    creator: String,
    rarity: String,  // Comum, Raro, Épico, Lendário
}
```

#### Função mint atualizada:
```move
entry fun mint(
    name: vector<u8>,
    description: vector<u8>,
    url: vector<u8>,
    creator: vector<u8>,
    rarity: vector<u8>,  // NOVO!
    ctx: &mut TxContext
) {
    let nft = MeuNFT {
        id: object::new(ctx),
        name: string::utf8(name),
        description: string::utf8(description),
        url: string::utf8(url),
        creator: string::utf8(creator),
        rarity: string::utf8(rarity),
    };
    transfer::public_transfer(nft, tx_context::sender(ctx));
}
```

#### Teste com raridade:
```bash
# NFT Comum
sui client call --function mint --module meu_nft --package [PACKAGE_ID] \
--args "Paisagem #1" "Uma bela paisagem" "https://exemplo.com" "Maria" "Comum" \
--gas-budget 10000000

# NFT Lendário
sui client call --function mint --module meu_nft --package [PACKAGE_ID] \
--args "Dragão Dourado" "NFT ultra raro" "https://exemplo.com" "Pedro" "Lendário" \
--gas-budget 10000000
```

---

## 🔴 EXERCÍCIOS AVANÇADOS

### 5. 🏷️ Sistema de Tags/Categorias

```move
use std::vector;

public struct MeuNFT has key, store {
    id: UID,
    name: String,
    description: String,
    url: String,
    creator: String,
    rarity: String,
    tags: vector<String>,  // Lista de tags: ["arte", "digital", "azul"]
}
```

#### Função helper para tags:
```move
fun create_tags(tag_bytes: vector<vector<u8>>): vector<String> {
    let mut tags = vector::empty<String>();
    let mut i = 0;
    while (i < vector::length(&tag_bytes)) {
        let tag = vector::borrow(&tag_bytes, i);
        vector::push_back(&mut tags, string::utf8(*tag));
        i = i + 1;
    };
    tags
}
```

#### Função mint com tags:
```move
entry fun mint_with_tags(
    name: vector<u8>,
    description: vector<u8>,
    url: vector<u8>,
    creator: vector<u8>,
    rarity: vector<u8>,
    tags: vector<vector<u8>>,  // [b"arte", b"digital", b"azul"]
    ctx: &mut TxContext
) {
    let nft = MeuNFT {
        id: object::new(ctx),
        name: string::utf8(name),
        description: string::utf8(description),
        url: string::utf8(url),
        creator: string::utf8(creator),
        rarity: string::utf8(rarity),
        tags: create_tags(tags),
    };
    transfer::public_transfer(nft, tx_context::sender(ctx));
}
```

### 6. 📊 Contador de NFTs Criados

```move
// Adicionar no topo do módulo
public struct NFTStats has key {
    id: UID,
    total_created: u64,
    creator_count: u64,
}

// Função para inicializar stats
entry fun init_stats(ctx: &mut TxContext) {
    let stats = NFTStats {
        id: object::new(ctx),
        total_created: 0,
        creator_count: 0,
    };
    transfer::share_object(stats);
}

// Modificar função mint para atualizar stats
entry fun mint_with_stats(
    stats: &mut NFTStats,
    name: vector<u8>,
    description: vector<u8>,
    url: vector<u8>,
    ctx: &mut TxContext
) {
    // Incrementar contador
    stats.total_created = stats.total_created + 1;
    
    let nft = MeuNFT {
        id: object::new(ctx),
        name: string::utf8(name),
        description: string::utf8(description),
        url: string::utf8(url),
    };
    transfer::public_transfer(nft, tx_context::sender(ctx));
}
```

---

## 🎮 DESAFIOS CRIATIVOS

### Desafio 1: 🎨 Coleção Temática
Crie 5 NFTs com tema único (ex: "Cores do Arco-íris")
```bash
# Vermelho
--args "Arco-iris Vermelho" "A cor da paixão" "https://via.placeholder.com/400x400/ff0000/ffffff?text=Vermelho" "Seu Nome" "Comum"

# Azul  
--args "Arco-iris Azul" "A cor da serenidade" "https://via.placeholder.com/400x400/0000ff/ffffff?text=Azul" "Seu Nome" "Comum"

# ... continue com outras cores
```

### Desafio 2: 🏆 NFT com Metadata Rica
Crie um NFT que conte uma história:
```move
public struct HistoryNFT has key, store {
    id: UID,
    title: String,
    story: String,        // História longa
    chapter: u64,         // Capítulo da história
    character: String,    // Personagem principal
    location: String,     // Onde se passa
    mood: String,         // Tom da história
    image_url: String,
}
```

### Desafio 3: 🎲 NFT Randomizado
Adicione elementos aleatórios baseados no timestamp:
```move
use sui::clock::{Self, Clock};

entry fun mint_random(
    base_name: vector<u8>,
    ctx: &mut TxContext,
    clock: &Clock
) {
    let timestamp = clock::timestamp_ms(clock);
    let random_suffix = timestamp % 1000;  // Número entre 0-999
    
    let name = string::utf8(base_name);
    string::append(&mut name, string::utf8(b" #"));
    string::append(&mut name, to_string(random_suffix));
    
    // ... resto da função
}
```

---

## 🔧 TEMPLATES PRONTOS

### Template 1: NFT de Arte Digital
```move
public struct DigitalArt has key, store {
    id: UID,
    title: String,
    artist: String,
    technique: String,    // "Digital Painting", "3D Render", etc.
    dimensions: String,   // "1920x1080", "4K", etc.
    year_created: String,
    image_url: String,
    edition_number: u64,  // 1 de 100, 2 de 100, etc.
    total_editions: u64,
}
```

### Template 2: NFT de Música
```move
public struct MusicNFT has key, store {
    id: UID,
    song_title: String,
    artist: String,
    genre: String,
    duration: String,     // "3:45"
    bpm: u64,            // Batidas por minuto
    key_signature: String, // "C Major"
    release_year: String,
    cover_art_url: String,
    audio_preview_url: String,
}
```

### Template 3: NFT de Colecionável
```move
public struct Collectible has key, store {
    id: UID,
    name: String,
    series: String,       // "Series 1", "Genesis", etc.
    rarity_level: u8,     // 1-5 (1=comum, 5=ultra raro)
    special_ability: String,
    power_level: u64,
    background_color: String,
    character_type: String,
    image_url: String,
    mint_number: u64,     // Número sequencial de criação
}
```

---

## 📋 Checklist de Modificações

### ✅ Para cada nova propriedade:
- [ ] Adicionar na struct
- [ ] Adicionar na função mint (parâmetro)
- [ ] Adicionar na criação do objeto
- [ ] Atualizar o display (se quiser mostrar)
- [ ] Recompilar e republicar
- [ ] Testar com comandos

### ✅ Teste sempre:
```bash
# Após modificar
sui move build

# Se compilou ok
sui client publish --gas-budget 100000000

# Criar display novamente
sui client call --function create_display ...

# Testar mint
sui client call --function mint ...
```

---

## 🎉 SHOWCASE FINAL

### Apresente seu NFT único!
1. **Mostre seu código modificado**
2. **Explique suas adições**
3. **Demonstre seu NFT criado**
4. **Compartilhe o Object ID** para outros verem

### Como verificar resultado:
```bash
# Ver seu NFT
sui client object [OBJECT_ID]

# Ver no explorer
# https://suiexplorer.com/object/[OBJECT_ID]?network=devnet
```

---

**🚀 Continue experimentando! A blockchain é sua para explorar!**
