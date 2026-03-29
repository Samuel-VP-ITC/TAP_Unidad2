# TAP_Unidad2
Este repositorio contiene la documentación técnica y ejemplos de código para el estudio de la modularidad y extensibilidad en software.
TAP_Unidad2_Componentes_Librerias
Este repositorio contiene la documentación técnica y ejemplos de código para el estudio de la modularidad y extensibilidad en software.

📖 2.1 Definición Conceptual: Componentes, Paquetes y Librerías
En la arquitectura de software moderna, la reutilización es clave.

Componente: Es una unidad modular de un sistema que encapsula su contenido y su ejecución es independiente del entorno, comunicándose a través de interfaces.

Paquete: Es un contenedor de módulos relacionados. En Python, cualquier directorio con un archivo __init__.py se considera un paquete.

Librería (Gema: Matplotlib): Es una colección de funciones y métodos que permiten realizar tareas específicas sin escribir el código desde cero.

Nota sobre Matplotlib: Es la librería estándar para la creación de gráficos estáticos, animados e interactivos en Python. En TAP, se usa para representar datos de sensores o métricas de usuario.

💻 2.2 Uso de Librerías Proporcionadas por el Lenguaje
Python ofrece una robusta "Standard Library". Para los proyectos de clase, las más utilizadas son math, datetime, y en el caso de GUIs avanzadas, la integración de Matplotlib con Flet mediante el control MatplotlibChart.

Ejemplo de implementación (Gráfico de Líneas):

Python
```
import flet as ft
import matplotlib.pyplot as plt
import numpy as np

def main(page: ft.Page):
    # Configuración de Matplotlib
    fig, ax = plt.subplots()
    x = np.linspace(0, 10, 100)
    y = np.sin(x)
    ax.plot(x, y)
    ax.set_title("Gráfico de Seno (Librería Externa)")

    # Integración en Flet
    chart = ft.MatplotlibChart(fig, expand=True)
    
    page.add(chart)

ft.app(target=main)
```

🛠️ 2.3 Creación de Componentes Definidos por el Usuario
Los componentes se dividen en dos categorías según su interacción con el usuario:

Visuales: Heredan de clases base de UI (ej. ft.Container o ft.UserControl). Poseen una representación gráfica.

No Visuales: Clases lógicas que gestionan datos, conexiones a BD o cálculos, sin renderizar elementos en pantalla.

Código de ejemplo (Componente Visual "Tarjeta de Usuario"):

Python
```
import flet as ft

class UserCard(ft.Container):
    def __init__(self, username, role):
        super().__init__()
        self.content = ft.Column([
            ft.Text(username, weight="bold", size=20),
            ft.Text(role, italic=True, color=ft.colors.GREY_500),
            ft.ElevatedButton("Ver Perfil")
        ])
        self.padding = 10
        self.border = ft.border.all(1, ft.colors.BLUE_200)
        self.border_radius = 10
```

📦 2.4 Creación y Uso de Paquetes Definidos por el Usuario
Para organizar un proyecto de TAP, se estructuran las funcionalidades en carpetas locales que luego se importan como librerías propias.

Estructura del Repositorio:

```
PROYECTO_FINAL/
│
├── main.py                # Punto de entrada
├── app_gui/               # PAQUETE VISUAL
│   ├── __init__.py
│   └── layouts.py
└── logic_tools/           # PAQUETE NO VISUAL
    ├── __init__.py
    └── calculator.py
```

Uso en main.py:

Python
```
from app_gui.layouts import main_screen
from logic_tools.calculator import process_data

# Aquí se ensambla la lógica con la interfaz
```

📚 Bibliografía (Formato APA)
Flet Dev. (2026). Matplotlib Chart Control. Recuperado de https://flet.dev/docs/controls/matplotlibchart/

Hunter, J. D. (2007). Matplotlib: A 2D graphics environment. Computing in Science & Engineering.

Python Software Foundation. (2026). Modules and Packages. Recuperado de https://docs.python.org/3/tutorial/modules.html

Van Rossum, G. (2023). The Python Library Reference. Python Documentation.
