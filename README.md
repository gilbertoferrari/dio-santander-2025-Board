<div align="center"><img align="center" width="40px" src="https://hermes.digitalinnovation.one/assets/diome/logo-minimized.png">Digital Innovation One</div>  

## :octocat: Sobre mim
Meu nome é **Gilberto Ferrari**<br/>
Sou um iniciante em programação e estou atualmente realizando uma trilha de aprendizado, com o foco em desenvolvimento **back-end** usando a linguagem **Java**<br/>

## Criando um board de tarefas Java  

```mermaid
classDiagram
    BoardEntity  "1" <|--|> "n" BoardColumnEntity
    BoardColumnEntity  "1" <|--|> "n" CardEntity
    CardEntity  "1"<|--|> "n" BlockEntity
    BoardColumnKindEnum  "1" <|--|>  "1" BoardColumnEntity
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
