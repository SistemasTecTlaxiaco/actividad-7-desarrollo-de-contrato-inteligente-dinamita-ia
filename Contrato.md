# 🚀 Sprint 3 - Smart Contract en Soroban (Stellar)

## 📌 Definición del Sprint
El objetivo principal de este sprint es lograr el *despliegue exitoso de un Smart Contract funcional en la red de prueba (Testnet) de Stellar*, utilizando Soroban y Rust.

Se busca que el contrato sea capaz de:
- Ejecutar lógica de negocio real
- Interactuar con la blockchain
- Ser invocado mediante la CLI de Stellar

---

## 🧠 Descripción del Contrato

Se desarrolló un contrato inteligente tipo *Escrow (custodia)* que permite:

- Depositar fondos (simulación de bloqueo de activos)
- Liberar fondos a un destinatario autorizado
- Consultar el estado de la transacción

### ⚙️ Funciones implementadas
- deposit: Registra una transacción de custodia
- release: Libera los fondos al vendedor
- get_escrow: Consulta el estado actual

---

## ✅ Criterios de Aceptación

### ✔ Lógica del contrato
- Implementación correcta de un flujo de custodia
- Separación clara de responsabilidades (depositar, liberar, consultar)
- Uso de estructuras de datos para persistencia

---

### 🔐 Seguridad

Se aplicaron buenas prácticas de seguridad en blockchain:

- *Autenticación obligatoria* con require_auth()
- Prevención de doble ejecución (double spending)
- Validación de estados antes de ejecutar operaciones

> Nota: Soroban maneja internamente aspectos como reentrancy, pero se diseñó el contrato evitando patrones inseguros.

---

### 🧪 Pruebas

- Compilación exitosa a WASM
- Ejecución en entorno local
- Despliegue en Testnet
- Invocación de funciones mediante CLI

---

## ⚙️ Configuración del SDK

### 🛠 Herramientas utilizadas
- Rust
- Soroban SDK
- Stellar CLI (stellar-cli)

---

### 🔧 Configuración del entorno

```bash
# Crear contrato
stellar contract init

# Compilar contrato
stellar contract build
