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


# Link del repositorio
https://github.com/IrvinSanchez-dev/Api-contract-stellar


# 🧩 1. Integridad del Despliegue (TestNet)

El contrato inteligente fue desarrollado y desplegado en la red de prueba oficial de Stellar (TestNet), utilizando el entorno de Soroban.

El despliegue permite la ejecución de funciones del contrato mediante un identificador único (**Contract ID**), el cual puede ser consultado y verificado en un explorador de bloques de Stellar.

## 🔹 Despliegue

    // Crear depósito en custodia
    pub fn deposit(
        env: Env,
        buyer: Address,
        seller: Address,
        token: Address,
        amount: i128,
    ) {
        buyer.require_auth();

        let token_client = TokenClient::new(&env, &token);

        // Transferir tokens al contrato
        token_client.transfer(&buyer, &env.current_contract_address(), &amount);

        let escrow = Escrow {
            buyer,
            seller,
            amount,
            released: false,
        };

        env.storage().instance().set(&DataKey::Escrow, &escrow);
    }

    // Liberar fondos al vendedor
    pub fn release(env: Env, token: Address) {
        let mut escrow: Escrow = env
            .storage()
            .instance()
            .get(&DataKey::Escrow)
            .unwrap();

        escrow.buyer.require_auth();

        if escrow.released {
            panic!("Fondos ya liberados");
        }

        let token_client = TokenClient::new(&env, &token);

        token_client.transfer(
            &env.current_contract_address(),
            &escrow.seller,
            &escrow.amount,
        );

        escrow.released = true;
        env.storage().instance().set(&DataKey::Escrow, &escrow);
    }

    // Consultar estado
    pub fn get_escrow(env: Env) -> Escrow {
        env.storage().instance().get(&DataKey::Escrow).unwrap()
    }
}

---

# 🧪 4. Pruebas de Integración (End-to-End)

Se realizaron pruebas completas desde la API hasta la blockchain.

## 🔹 Flujo probado

1. Cliente realiza request
2. API procesa la solicitud
3. Se construye la transacción
4. Se envía a TestNet
5. Se obtiene hash


# Link del repositorio
https://github.com/IrvinSanchez-dev/Api-contract-stellar




