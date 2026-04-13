# Pack de Atualizações - Samuelson Rosa

Repositório de packs de atualização para o sistema de gestão jurídica.

## Estrutura

```
pack-advogado/
├── packs/
│   ├── v1.0.1.json
│   ├── v1.1.0.json
│   └── v2.0.0.json
├── latest.json          -> Link para o pack mais recente
├── pack.json            -> Pack atual (cópia do latest)
└── README.md
```

## Como criar um novo pack

1. Crie um arquivo `packs/vX.Y.Z.json` com as alterações
2. Atualize o `latest.json` para apontar para o novo pack
3. Commit e push

## Exemplo de pack

```json
{
  "version": "1.0.1",
  "build": 2,
  "releaseDate": "2026-04-14",
  "checksum": "sha256_hash_aqui",
  "changes": [
    {
      "type": "file-update",
      "file": "src/client/components/common/Logo.tsx",
      "content": "...",
      "description": "Atualização do logo"
    },
    {
      "type": "sql",
      "sql": "ALTER TABLE clientes ADD COLUMN novo_campo VARCHAR(255);",
      "description": "Adição de novo campo na tabela clientes"
    }
  ],
  "newVersion": {
    "version": "1.0.1",
    "build": 2,
    "releaseDate": "2026-04-14"
  }
}
```

## Tipos de mudanças

| Tipo | Descrição |
|------|-----------|
| `file-update` | Atualiza um arquivo existente |
| `file-create` | Cria um novo arquivo |
| `file-delete` | Remove um arquivo |
| `sql` | Executa um comando SQL |
| `migration` | Executa uma migration no banco |

## Segurança

- Cada pack deve ter um checksum SHA-256
- O sistema verifica o checksum antes de aplicar
- Packs corrompidos são rejeitados automaticamente

## Licença

© 2026 Samuelson Rosa Advocacia & Consultoria Jurídica
