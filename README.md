<div align="center"><img align="center" width="40px" src="https://hermes.digitalinnovation.one/assets/diome/logo-minimized.png">Digital Innovation One</div>  

## Criando um board de tarefas Java  

```mermaid
classDiagram
    BoardEntity <|--|> BoardColumnEntity
    BoardColumnEntity <|--|> CardEntity
    CardEntity <|--|> BlockEntity
    BoardColumnKindEnum <|--|> BoardColumnEntity
    class BoardEntity {
        - Long id
        - String name
        - List~BoardColumnEntity~ boardColumns
        + BoardColumnEntity getInitialColumn()
        + BoardColumnEntity getCancelColumn()
        - BoardColumnEntity getFilteredColumn(Predicate~BoardColumnEntity~ filter)
    }

    class BoardColumnEntity {
        - Long id
        - String name
        - int order
        - BoardColumnKindEnum kind
        - BoardEntity board
        - List~CardEntity~ cards
    }

    class CardEntity {
        - Long id
        - String title
        - String description
        - BoardColumnEntity boardColumn
    }
    class BlockEntity {
        - Long id
        - OffsetDateTime blockedAt
        - String blockReason
        - OffsetDateTime unblockedAt
        - String unblockReason
    }

    class BoardColumnKindEnum {
        <<enum>>
        INITIAL
        FINAL
        CANCEL
        PENDING
        + static BoardColumnKindEnum findByName(String name)
    }
```
