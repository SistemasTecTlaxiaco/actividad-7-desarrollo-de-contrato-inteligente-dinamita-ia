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
```
# Implementación del contrato

### Primera actividad. Creacion de smart contract de transacciones.
<img width="1073" height="989" alt="image" src="https://github.com/user-attachments/assets/dfb1946d-7870-4aac-beea-04137c1e67db" />


<img width="910" height="392" alt="image" src="https://github.com/user-attachments/assets/8d34e494-8ffc-4a23-8a85-abcd7c328d89" />

###Segunda actividad. Despliegue a tesnet.
<img width="1134" height="828" alt="image" src="https://github.com/user-attachments/assets/bef64747-c620-4a3c-9377-ec941a13b5d8" />

<img width="981" height="893" alt="image" src="https://github.com/user-attachments/assets/217ec7a2-0ebf-4d7d-9584-a285dc5c49c2" />

