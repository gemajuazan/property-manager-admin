# FincaManager

> Aplicación Android para la gestión integral del trabajo diario de administradores de fincas y comunidades de propietarios.

---

## Descripción

**FincaManager** es una aplicación móvil nativa para Android orientada a profesionales de la administración de fincas. Centraliza la gestión de tareas, incidencias, facturación y comunicaciones, y ofrece reportes mensuales del trabajo desarrollado para facilitar el seguimiento y la rendición de cuentas ante las comunidades.

---

## Funcionalidades principales

### Gestión de tareas e incidencias
- Creación y seguimiento de tareas con tipo (`llamada`, `incidencia`, `visita`, `gestión`, `reunión`)
- Asignación de prioridad, finca asociada y fecha límite
- Historial de cambios y notas por tarea
- Adjunto de fotos desde cámara o galería
- Filtrado y búsqueda avanzada por estado, tipo y finca

### Fincas y propietarios
- Directorio de comunidades gestionadas
- Ficha de cada propietario con datos de contacto, vivienda y cuota
- Asociación de tareas, facturas e incidencias por finca
- Gestión de documentación de cada comunidad

### Facturación
- Emisión de facturas y presupuestos por comunidad o propietario
- Estados de factura: `borrador` → `emitida` → `pagada` / `vencida`
- Plantillas reutilizables
- Exportación a PDF

### Reportes mensuales
- Resumen de tareas cerradas por tipo y período
- Tiempo medio de resolución de incidencias
- Facturación emitida vs. cobrada
- Incidencias abiertas y pendientes de resolución
- Gráficas interactivas exportables

### Avisos y recordatorios
- Notificaciones push (FCM) para eventos importantes
- Recordatorios locales para vencimientos y reuniones de comunidad
- Alertas de tareas próximas a su fecha límite

---

## Arquitectura

El proyecto sigue los principios de **Clean Architecture** combinados con el patrón **MVVM**, organizados en módulos Gradle independientes para favorecer la escalabilidad y la separación de responsabilidades.

```
FincaManager/
├── app/                        # Módulo de ensamblado principal
├── feature/
│   ├── tareas/                 # Gestión de tareas e incidencias
│   ├── facturacion/            # Facturación y presupuestos
│   ├── fincas/                 # Fincas y propietarios
│   ├── reportes/               # Reportes y analíticas
│   └── avisos/                 # Notificaciones y recordatorios
└── core/
    ├── domain/                 # Entidades + casos de uso (puro Kotlin)
    ├── data/                   # Repositorios, Room, Retrofit, mappers
    ├── ui/                     # Componentes Compose compartidos
    └── common/                 # Utilidades comunes
```

### Flujo de datos por módulo

```
Composable (View)
    ↕ StateFlow / UiState
ViewModel
    ↕ suspend fun / Flow
UseCase  (dominio)
    ↕ interfaz Repository
RepositoryImpl
    ↕                  ↕
Room (local)     Retrofit (remoto)
```

---

## Stack tecnológico

| Área | Tecnología |
|---|---|
| Lenguaje | Kotlin |
| UI | Jetpack Compose + Material 3 |
| Navegación | Navigation Compose |
| Inyección de dependencias | Hilt |
| Base de datos local | Room (SQLite) |
| Preferencias | DataStore Preferences |
| Red | Retrofit 2 + OkHttp |
| Serialización | Kotlin Serialization |
| Asincronía | Kotlin Coroutines + Flow |
| Tareas en segundo plano | WorkManager |
| Notificaciones push | Firebase Cloud Messaging (FCM) |
| Gráficas | Vico |
| Generación de PDF | Android PdfDocument / iText |
| Autenticación local | BiometricPrompt |
| Tests | JUnit 4/5, MockK, Turbine |

---

## Primeros pasos

### Requisitos previos

- Android Studio Hedgehog (2023.1.1) o superior
- JDK 17
- Android SDK 34
- Kotlin 1.9+

### Instalación

```bash
# Clona el repositorio
git clone https://github.com/tu-usuario/finca-manager.git
cd finca-manager

# Abre en Android Studio o compila desde línea de comandos
./gradlew assembleDebug
```
---

## Capturas de pantalla

> *(Próximamente)*

---

## Hoja de ruta

### MVP — v1.0
- [x] Arquitectura base y módulos Gradle
- [ ] Módulo de fincas y propietarios
- [ ] Módulo de tareas e incidencias
- [ ] Reportes básicos mensuales

### v1.1
- [ ] Módulo de facturación completo
- [ ] Exportación a PDF
- [ ] Notificaciones y recordatorios

### v2.0
- [ ] Sincronización con servidor remoto
- [ ] Acceso web complementario
- [ ] Multiusuario / modo equipo

---

## Tests

```bash
# Tests unitarios
./gradlew test

# Tests de instrumentación (requiere emulador o dispositivo)
./gradlew connectedAndroidTest

# Cobertura
./gradlew jacocoTestReport
```

---

## Contribuciones

Las contribuciones son bienvenidas. Por favor:

1. Haz un fork del repositorio
2. Crea una rama para tu funcionalidad: `git checkout -b feature/nombre-funcionalidad`
3. Aplica los commits con mensajes descriptivos siguiendo [Conventional Commits](https://www.conventionalcommits.org/)
4. Abre un Pull Request describiendo los cambios

---

## Autor

Desarrollado con ❤️ para simplificar el trabajo de los administradores de fincas.

---