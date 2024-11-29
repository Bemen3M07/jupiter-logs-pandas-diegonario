## Exercici 1: Comandes per treballar amb logs

### Veure contínuament els logs


Per visualitzar contínuament els logs que es van escrivint en un fitxer, es pot utilitzar la següent comanda de Linux:

```bash
tail -f fitxer.log

grep "paraula" fitxer.log
```


## Exercici 2: Configuració del Logging

### Configuració dels Handlers i Formatters
A continuació es mostra com configurar el sistema de logging per separar els missatges en fitxers segons el nivell de gravetat (INFO i ERROR) i com afegir un handler amb format CSV.

```python
import logging
```

# Handlers
info_handler = logging.FileHandler('info.log')
error_handler = logging.FileHandler('error.log')
csv_handler = logging.FileHandler('logs.csv')

# Formatters
info_handler.setFormatter(logging.Formatter('%(asctime)s - %(levelname)s - %(message)s'))
error_handler.setFormatter(logging.Formatter('%(asctime)s - %(levelname)s - %(message)s'))
csv_handler.setFormatter(logging.Formatter('%(asctime)s,%(levelname)s,%(message)s'))

# Loggers
logger = logging.getLogger('main')
logger.setLevel(logging.DEBUG)
logger.addHandler(info_handler)
logger.addHandler(error_handler)
logger.addHandler(csv_handler)

# Exemple de missatges
logger.info('Aquest és un missatge d\'info')
logger.error('Aquest és un missatge d\'error')

---

### Resposta a les preguntes

#### Què és millor, mostrar els logs a la terminal o bolcar-los a un fitxer?

**Resposta**:
- Mostrar els logs a la terminal és útil durant el desenvolupament perquè et permet veure els errors en temps real.
- Bolcar els logs a un fitxer és essencial en producció perquè es poden analitzar posteriorment i es manté un registre històric dels esdeveniments.

---

#### Avantatges i desavantatges de diferents configuracions

| Configuració                                           | Avantatges                                                                                               | Desavantatges                                                                                     |
|--------------------------------------------------------|----------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| **Fent servir la configuració per defecte del mòdul logging**       | Senzill i ràpid d’implementar.                                                                           | Poc flexible per personalitzar formatadors i handlers.                                           |
| **Instanciant un objecte logger i parametritzant-lo des del programa** | Permet gran flexibilitat per personalitzar format, nivells i destinació dels logs.                       | Requereix més codi i coneixement avançat del mòdul logging.                                      |
| **Instanciant un objecte logger a partir d’una configuració emmagatzemada a fitxer** | Centralitza la configuració i facilita la modificació sense canviar el codi del programa.                | Pot ser més difícil de configurar inicialment i necessita fitxers de configuració addicionals.   |

---

---

## Llibreries de logging en altres llenguatges

### Taula comparativa

| Característica                                | Llenguatge 1: Java                       | Llenguatge 2: JavaScript                  |
|----------------------------------------------|------------------------------------------|------------------------------------------|
| **Nom de la llibreria**                      | Log4j                                    | Winston                                  |
| **És nativa del llenguatge?**                | No, però és molt utilitzada              | No, és una llibreria externa             |
| **URL per descarregar-se la llibreria**      | [https://logging.apache.org/log4j/2.x/](https://logging.apache.org/log4j/2.x/) | [https://github.com/winstonjs/winston](https://github.com/winstonjs/winston) |
| **Inicialització de l’objecte de logger**    | `Logger logger = LogManager.getLogger();` | `const logger = winston.createLogger({...});` |
| **Nivells de log disponibles**               | TRACE, DEBUG, INFO, WARN, ERROR, FATAL   | error, warn, info, http, verbose, debug, silly |
| **Mètode per fer log**                       | `logger.info("Missatge");`               | `logger.info("Missatge");`               |
| **Tipus de manegadors**                      | ConsoleAppender, FileAppender, etc.      | Console, File, HTTP                      |
| **Opcions de format**                        | Configuració XML o programàtica          | Personalització amb formatadors com `winston.format.combine` |

---

### Exemple d'inicialització i ús

#### **Log4j (Java)**

```java
import org.apache.logging.log4j.LogManager;
import org.apache.logging.log4j.Logger;

public class Main {
    private static final Logger logger = LogManager.getLogger();

    public static void main(String[] args) {
        logger.info("Això és un missatge d'INFO");
        logger.error("Això és un missatge d'ERROR");
    }
}














