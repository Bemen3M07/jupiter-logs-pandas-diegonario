## Exercici 1: Comandes per treballar amb logs

### Veure contínuament els logs


Per visualitzar contínuament els logs que es van escrivint en un fitxer, es pot utilitzar la següent comanda de Linux:

```bash
tail -f fitxer.log

grep "paraula" fitxer.log



## Exercici 2: Configuració del Logging

### Configuració dels Handlers i Formatters
A continuació es mostra com configurar el sistema de logging per separar els missatges en fitxers segons el nivell de gravetat (INFO i ERROR) i com afegir un handler amb format CSV.

```python
import logging

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












