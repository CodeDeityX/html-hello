# AgentHub - Especificaciones Técnicas del Panel de Administración (SPECS.md)

## 1. Descripción del Producto
**AgentHub** es una plataforma SaaS B2B dirigida a empresas que necesitan alquilar, desplegar y supervisar asistentes de inteligencia artificial (agentes). El usuario administrador del panel requiere una interfaz clara, responsiva y de alta densidad de información para controlar métricas financieras, flujos de usuarios, asignación de skills, auditoría de contratos y registros de errores en tiempo real.

## 2. Stack Tecnológico y Restricciones
- **Estructura:** HTML5 semántico (`<header>`, `<nav>`, `<main>`, `<section>`, `<table>`).
- **Estilos:** Tailwind CSS v4 cargado exclusivamente vía CDN oficial (`https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4`). Prohibido usar archivos CSS externos o estilos en línea (`style="..."`).
- **Interactividad:** JavaScript vainilla (Vanilla JS) embebido, sin frameworks externos (React, Vue, etc.) ni librerías de terceros (jQuery).

---

## 3. Especificaciones por Sección (Al menos 3 por vista)

### 3.1. Dashboard
1. **Tarjetas de Métricas:** Cuatro tarjetas dispuestas en una rejilla responsiva de 2 columnas en tablet y 4 en escritorio. Cada tarjeta incluye un icono, etiqueta y un valor hardcodeado (Ingresos Totales, Pérdidas por Descuentos, Agentes Activos, Agentes Fallando).
2. **Gráfico de Actividad Semanal:** Un contenedor de ancho completo debajo de las tarjetas métricas, estructurado con un borde discontinuo (`border-dashed`) y una etiqueta centrada.
3. **Indicadores de Alerta:** Las tarjetas de agentes fallando incluyen un badge de alerta parpadeante en tono rojo.

### 3.2. Gestión de Usuarios
1. **Tabla de Registros:** Tabla HTML semántica con al menos 5 filas de datos hardcodeados que detallan nombre, correo, plan y estado.
2. **Dropdown de Acciones:** Botón de activación con icono de tres puntos (`⋮`) que despliega un menú flotante con "Ver detalle" y "Eliminar".
3. **Modal de Detalle:** Componente modal superpuesto (*overlay*) que se abre al hacer clic en "Ver detalle" y se cierra con botón o clic en el *backdrop*.

### 3.3. Gestión de Agentes
1. **Listado de Agentes:** Panel con al menos 4 agentes activos, mostrando nombre, propietario, estado y control expandible.
2. **Listas Colapsables de Skills:** Las skills asociadas están ocultas por defecto y se despliegan mediante transición suave al expandir.
3. **Modal de Configuración:** El menú de acciones incluye "Configurar", abriendo un modal con el prompt de sistema editable en un `<textarea>`.

### 3.4. Skills (Catálogo)
1. **Catálogo de Capacidades:** Cuadrícula con al menos 4 skills disponibles, descripción y contador de agentes habilitados.
2. **Bloque Explicativo:** Sección informativa que define conceptualmente qué significa una "skill" en AgentHub.
3. **Acciones de Mantenimiento:** Menú desplegable (`⋮`) con "Ver detalle" y "Eliminar" por cada skill.

### 3.5. Contrataciones de Agentes
1. **Tabla de Contratos:** Listado tabular con al menos 4 contratos activos y pasados (cliente, agente, skills, fechas, importe).
2. **Desglose Financiero en Modal:** "Ver detalle" abre un modal con el desglose de precios unitarios de cada skill contratada.
3. **Filtros de Estado:** Cabecera con diferenciación rápida de contratos vigentes y finalizados.

### 3.6. Log de Errores
1. **Registro de Incidencias:** Tabla de errores con al menos 6 entradas (timestamp, agente, tipo, descripción).
2. **Badges de Gravedad:** Etiquetas con códigos de color según severidad (Crítico, Advertencia, Info).
3. **Traza y Resolución:** Menú contextual con opción para ver traza completa en modal o marcar como resuelto.

---

## 4. Inventario de Componentes UI Reutilizables
- **Sidebar de Navegación:** Barra lateral fija con enlaces y estado activo.
- **Header Superior:** Cabecera con título de sección, perfil y botón de toggle para Modo Oscuro.
- **Dropdown de Acciones (`⋮`):** Menú flotante contextual.
- **Componente Modal (Overlay):** Ventana emergente con fondo translúcido (*backdrop*).
- **Badge de Estado:** Etiqueta compacta con colores condicionales.
- **Lista Colapsable:** Contenedor de expansión vertical con animación.

## 5. Criterios de Aceptación (Condiciones Verificables)
1. **[Git History]** El archivo `SPECS.md` debe estar commiteado en el repositorio de manera independiente **antes** de añadir cualquier archivo HTML.
2. **[Navegación]** Las seis secciones del panel son accesibles desde la barra lateral.
3. **[Modo Oscuro]** El toggle conmuta los esquemas de color usando las clases `dark:` de Tailwind.
4. **[Dropdowns Funcionales]** Los menús de acciones (`⋮`) se abren y cierran al hacer clic fuera.
5. **[Modales Interactivos]** Los modales se abren y cierran mediante botón o clic en el *backdrop*.
6. **[Listas Colapsables]** Las skills responden expandiéndose o contrayéndose con transición fluida.
