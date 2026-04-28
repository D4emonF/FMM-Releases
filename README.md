# FiveM Mod Manager

Aplicativo desktop para gerenciar mods do FiveM com um clique.

## 📁 Estrutura de Pastas dos Mods

Configure no app a pasta base dos mods (ex: `E:/FiveM/Mods`) e organize assim:

```
Mods/ (E:/FiveM/Mods)
├── Sons/
│   ├── CSGO/
│   │   └── pack.awc
│   └── Valorant/
│       └── pack.awc
├── RPF/
│   ├── Estradas/              ← Categoria
│   │   ├── Estrada 1/         ← Mod individual
│   │   ├── Estrada 2/
│   │   └── Estrada 3/
│   ├── Postes de Luz/
│   │   ├── LED Azul/
│   │   └── LED Branco/
│   └── Veiculos/
│       └── Pack Carros/
└── CitizenExtras/
    ├── Efeitos/
    │   ├── Confetes/
    │   └── Particulas/
    └── HUD/
        └── CustomV2/

Citizens/ (E:/Jogos/FiveM/Citizens) ← SUAS CITIZENS PARA ATIVAR
├── [ MASSINHA DARK ]/
│   └── citizen/               ← Pasta citizen completa
├── [ ORIGINAL ]/
│   └── citizen/
└── [ LEAN ]/
    └── citizen/
```

## ⚙️ Configurações necessárias

| Campo | Exemplo | Nota |
|-------|---------|------|
| Pasta do GTA V | `C:/Games/Grand Theft Auto V` | Necessária apenas para mods de som |
| Pasta do FiveM | `C:/Users/SeuUser/AppData/Local/FiveM/FiveM.app` | Obrigatória |
| Pasta dos Mods | `E:/FiveM/Mods` | Para Sons, RPF e CitizenExtras |
| **Pasta de Citizens** | `E:/Jogos/FiveM/Citizens` | 🔴 **IMPORTANTE**: Aqui você guarda suas citizens para ativar/desativar |
| Pasta de Backup | `E:/FiveM/Backups` | Opcional - backup automático antes de substituir |

## 🔒 Backup Automático

Antes de qualquer substituição, o app tenta fazer backup automático da pasta de destino em:
```
Backups/YYYYMMDD_HHMMSS/
```

Se o backup falhar por falta de permissões, o app **continua funcionando normalmente** — o backup é apenas uma medida de segurança, não é crítico.

## 🛡️ Permissões de Admin

Se o Windows pedir permissão ao alterar arquivos no disco E:

**Opção 1: Executar o app como Admin** (Recomendado)
- Clique direito no `FiveMModManager.exe` → "Executar como administrador"
- Ou crie um atalho com a propriedade "Executar como administrador"

**Opção 2: Desabilitar controle de acesso da pasta**
- Clique direito em `E:/Jogos/` → Propriedades → Segurança → Editar
- Selecione seu usuário → marque "Controle Total" → Aplicar → OK

**Opção 3: Usar PowerShell (como Admin)**
```powershell
icacls "E:\Jogos\FiveM" /grant "%USERNAME%":F /t /c
icacls "E:\Jogos\FiveM\Backups" /grant "%USERNAME%":F /t /c
```

## 📋 Logs

Todas as ações ficam registradas na aba **Histórico** e no arquivo `fmm_log.json` ao lado do executável.

## 🎯 Como funciona cada tipo de mod

| Tipo | O que faz ao ativar | O que faz ao desativar |
|------|---------------------|------------------------|
| **Som** | Copia arquivo para pasta do GTA V | Remove o arquivo |
| **RPF** | Copia pasta para `FiveM/mods/` | Remove pasta de `FiveM/mods/` |
| **Citizen** | Remove citizen atual, copia nova | Remove citizen da pasta FiveM |
| **Extras** | Copia/sobrescreve arquivos dentro da citizen | Remove apenas os arquivos do extra |
