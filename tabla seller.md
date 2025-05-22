# **`APLICANDO LOS CONVENTIONAL COMMITS part 1`**

*Sigue estos pasos para sacar 20 xdddd*

## En este primera parte todo te va a salir error o te marcara rojo
## No lo soluciones solo sigue los pasos
## Sigue los pasos crjo
## Aqui tambien estan las solucciones 
## Tu solo sigue los pasos

![image](https://github.com/user-attachments/assets/37dca32b-c177-42c9-9e5f-eb3357f41460)


## **Primero creamos la rama feature**

Crea un codespace nuevo y en la terminal coloca 

### **git checkout -b feature/sp3_u3_seller**

y trae los archivos de la rama **develop** con

### **git pull origin develop**

Una vez echo todo eso ahora colocaremos los contenidos a cada carpeta correspondiente para nuestro proyecto back-end

entramos a la carpeta
**SRC**
└── **main**
    └── **java**
        └── **pe**
            └── **edu**
                └── **vellegrande**
                    └── **project**


Veremos cuatro carpetas                             

![Captura de pantalla 2025-05-22 a las 3 47 04 a  m](https://github.com/user-attachments/assets/ea25dd4c-162c-41f6-b630-3cb23f9c499f)

# MODEL

### **Dentro de la carpeta model** crea un archivo nuevo llamado **Seller.java** 

y dentro de el colocaras 

```java
package pe.edu.vallegrande.project.model;

import lombok.Data;
import jakarta.persistence.Entity;
import jakarta.persistence.GeneratedValue;
import jakarta.persistence.GenerationType;
import jakarta.persistence.Id;
import jakarta.persistence.Column;
import jakarta.persistence.Table;

@Entity
@Data
@Table(name = "seller")
public class Seller {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    @Column(name = "id")
    private Long id;

    @Column(name = "name")
    private String name;

    @Column(name = "last_name")
    private String lastName;

    @Column(name = "email")
    private String email;

    @Column(name = "phone")
    private String phone;

    @Column(name = "state")
    private String state;
}
```

y en la **TERMINAL** colocaras ---> *git add .* y despues colocas

---> *git commit -m "feat: Seller entity and functionality with data records"*

# REPOSITORY

luego **Dentro de la carpeta repository** crea un archivo nuevo llamado **SellerRepository.java** 

y dentro de el colocaras

```java
package pe.edu.vallegrande.project.repository;

import pe.edu.vallegrande.project.model.Seller;
import org.springframework.data.jpa.repository.JpaRepository;

SellerRepository extends JpaRepository {
}
```

y en la **TERMINAL** colocaras ---> *git add .* y despues colocas

---> *git commit -m "feat: Added interface for Seller CRUD"*

# REST

luego **Dentro de la carpeta rest** crea un archivo nuevo llamado **SellerRest.java** 

y dentro de el colocaras

```java
package pe.edu.vallegrande.project.rest;

import pe.edu.vallegrande.project.model.Seller;
import pe.edu.vallegrande.project.service.SellerService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.*;

import java.util.List;
import java.util.Optional;

@CrossOrigin(origins = "*")
@RestController
@RequestMapping("/v1/api/seller")
public class SellerRest {


    @GetMapping("/{id}")
    public Optional<Seller> findById(@PathVariable Long id) {
        return sellerService.findById(id);
    }

    @PostMapping("/save")
    public Seller save(@RequestBody Seller seller) {
        return sellerService.save(seller);
    }

    @PutMapping("/update")
    public Seller update(@RequestBody Seller seller) {
        return sellerService.update(seller);
    }

    @DeleteMapping("/delete/{id}")
    public ResponseEntity<?> delete(@PathVariable Long id) {
        Optional<Seller> sellerOptional = sellerService.findById(id);
        sellerService.delete(sellerOptional.get());
        return ResponseEntity.ok("Vendedor desactivado con éxito.");
    }
}
```

y en la **TERMINAL** colocaras ---> **git add .** y despues colocas

---> **git commit -m "feat: Create an endpoint or controller for the Seller table with CRUD operations"**

# SERVICE

luego **Dentro de la carpeta service** crea un archivo nuevo llamado **SellerService.java** 

y dentro de el colocaras

```java
package pe.edu.vallegrande.project.service;

import pe.edu.vallegrande.project.model.Seller;
import java.util.List;
import java.util.Optional;

    Seller update(Seller seller);
    void delete(Seller seller);
}
```

y en la **TERMINAL** colocaras ---> *git add .* y despues colocas

---> **git commit -m "feat: Defines basic service operations for the Vendor entity"**

# IMPL

ahora dentro de la carpeta service veras otra carpeta llamada **impl** **Dentro de ella** crea un archivo nuevo llamado **SellerServiceImpl.java** 

y dentro de el colocaras

```java
package pe.edu.vallegrande.project.service.impl;

import pe.edu.vallegrande.project.model.Seller;
import pe.edu.vallegrande.project.repository.SellerRepository;
import pe.edu.vallegrande.project.service.SellerService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;
import lombok.extern.slf4j.Slf4j;
import java.util.List;
import java.util.Optional;

@Slf4j
@Service
public class SellerServiceImpl implements SellerService {

    private final SellerRepository sellerRepository;

    @Override
    public Optional<Seller> findById(Long id) {
        log.info("Buscando Vendedor por ID");
        return sellerRepository.findById(id);
    }

    @Override
    public Seller save(Seller seller) {
        log.info("Guardando vendedor: " + seller.toString());
        seller.setState("A");  // Estado activo
        return sellerRepository.save(seller);
    }

    @Override
    public Seller update(Seller seller) {
        log.info("Actualizando vendedor: " + seller.toString());
        seller.setState("A");  // Estado activo
        return sellerRepository.save(seller);
    }

er.setState("I");
        sellerRepository.save(seller); // Guardamos el vendedor con el estado actualizado
    }
}
```
y en la **TERMINAL** colocaras ---> *git add .* y despues colocas

---> **git commit -m "feat: Implementing SellerService with CRUD functionality"**

Debe verse asi 

![Captura de pantalla 2025-05-22 a las 4 48 22 a  m](https://github.com/user-attachments/assets/e308d891-9994-4fe6-af42-ebb4e3dd8cf9)

Ahora tendras que volver nuevamente a la carpeta main 

    **SRC**
    └── **main**

Donde veras una carpeta llamada **resources** 

![Captura de pantalla 2025-05-22 a las 4 59 15 a  m](https://github.com/user-attachments/assets/a300d28c-a669-4630-a3cb-548f85441a0d)

Deberas entrar a la carpeta **resources**

donde veras tres archivos y solo tocaras dos

![Captura de pantalla 2025-05-22 a las 5 01 22 a  m](https://github.com/user-attachments/assets/b2d1e85d-5d1f-4173-b0e5-e1a1c35990e9)

# SCHEMA.SQL

en el archivo **schema.sql** agregaras tu tabla **seller**

```sql
CREATE TABLE seller (
    id INT IDENTITY(1,1),
    name VARCHAR(100),
    last_name VARCHAR(100),
    dni CHAR(8),
    email VARCHAR(50),
    phone CHAR(9),
    state CHAR(1),
);
```
y en la **TERMINAL** colocaras ---> *git add .* y despues colocas

---> **git commit -m "feat: Seller table for data registration"**

# DATA.SQL

luego en el archivo **data.sql** agregaras los datos de tu tabla

```sql
INSERT INTO seller (name, last_name, dni, email, phone, state) VALUES
('Carlos', 'Pérez', '12345678', 'cperez@empresa.com', '987654321', 'A'),
('Lucía', 'Gómez', '87654321', 'lgomez@empresa.com', '912345678', 'A');
```
y en la **TERMINAL** colocaras ---> *git add .* y despues colocas

---> **git commit -m "chore: Insert initial data into the seller table"**

# **`APLICANDO LOS CONVENTIONAL COMMITS part 2`**
## Ahora vamo a actulizar los commits para que no digan que no hicimos ninguna mejora

![image](https://github.com/user-attachments/assets/c40ce974-7703-4974-aa72-8a1009c0900c)

### debes copiar todo lo que sigue ahora, porque lo de arriba todo esta mal solo era para tener algo xdd

![rata](https://github.com/user-attachments/assets/096dceaa-46ea-4ac9-8305-e1f12944215f)

# MODEL

### **Dentro de la carpeta model** tu archivo llamado **Seller.java** 

lo debes de mejorar (solo copia y pega todo ta craneado ya) 

```java
package pe.edu.vallegrande.project.model;

import lombok.Data;
import jakarta.persistence.Entity;
import jakarta.persistence.GeneratedValue;
import jakarta.persistence.GenerationType;
import jakarta.persistence.Id;
import jakarta.persistence.Column;
import jakarta.persistence.Table;

@Entity
@Data
@Table(name = "seller")
public class Seller {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    @Column(name = "id")
    private Long id;

    @Column(name = "name")
    private String name;

    @Column(name = "last_name")
    private String lastName;

    @Column(name = "dni", unique = true)
    private String dni;

    @Column(name = "email", unique = true)
    private String email;

    @Column(name = "phone", unique = true)
    private String phone;

    @Column(name = "state")
    private String state;
}
```

y en la **TERMINAL** colocaras ---> *git add .* y despues colocas

---> *git commit -m "refactor: Improved vendor file functionality in the model"*

# REPOSITORY

luego **Dentro de la carpeta repository** tu archivo llamado **SellerRepository.java** 

```java
package pe.edu.vallegrande.project.repository;

import pe.edu.vallegrande.project.model.Seller;
import org.springframework.data.jpa.repository.JpaRepository;

public interface SellerRepository extends JpaRepository<Seller, Long> {
}
```

y en la **TERMINAL** colocaras ---> *git add .* y despues colocas

---> *git commit -m "fix: Seller class mapped incorrectly"*

# REST

luego **Dentro de la carpeta rest** tu archivo llamado **SellerRest.java** 

```java
package pe.edu.vallegrande.project.rest;

import pe.edu.vallegrande.project.model.Seller;
import pe.edu.vallegrande.project.service.SellerService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.*;

import java.util.List;
import java.util.Optional;

@CrossOrigin(origins = "*")
@RestController
@RequestMapping("/v1/api/seller")
public class SellerRest {

    private final SellerService sellerService;

    @Autowired
    public SellerRest(SellerService sellerService) {
        this.sellerService = sellerService;
    }

    @GetMapping
    public List<Seller> findAll() {
        return sellerService.findAll();
    }

    @GetMapping("/{id}")
    public Optional<Seller> findById(@PathVariable Long id) {
        return sellerService.findById(id);
    }

    @PostMapping("/save")
    public Seller save(@RequestBody Seller seller) {
        return sellerService.save(seller);
    }

    @PutMapping("/update")
    public Seller update(@RequestBody Seller seller) {
        return sellerService.update(seller);
    }

    @DeleteMapping("/delete/{id}")
    public ResponseEntity<?> delete(@PathVariable Long id) {
        Optional<Seller> sellerOptional = sellerService.findById(id);
        sellerService.delete(sellerOptional.get());
        return ResponseEntity.ok("Vendedor desactivado con éxito.");
    }
}
```

y en la **TERMINAL** colocaras ---> **git add .** y despues colocas

---> **git commit -m "fix: correction of removed logical functionality"**

# SERVICE

luego **Dentro de la carpeta service** tu archivo llamado **SellerService.java** 

```java
package pe.edu.vallegrande.project.service;

import pe.edu.vallegrande.project.model.Seller;
import java.util.List;
import java.util.Optional;

public interface SellerService {

    List<Seller> findAll();
    Optional<Seller> findById(Long id);
    Seller save(Seller seller);
    Seller update(Seller seller);
    void delete(Seller seller);
}
```

y en la **TERMINAL** colocaras ---> *git add .* y despues colocas

---> **git commit -m "refactor: rename methods in SellerService for clarity"**

# IMPL

ahora en la carpeta llamada **impl** **Dentro de tu archivo** llamado **SellerServiceImpl.java** 


```java
package pe.edu.vallegrande.project.service.impl;

import pe.edu.vallegrande.project.model.Seller;
import pe.edu.vallegrande.project.repository.SellerRepository;
import pe.edu.vallegrande.project.service.SellerService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;
import lombok.extern.slf4j.Slf4j;
import java.util.List;
import java.util.Optional;

@Slf4j
@Service
public class SellerServiceImpl implements SellerService {

    private final SellerRepository sellerRepository;

    @Autowired
    public SellerServiceImpl(SellerRepository sellerRepository) {
        this.sellerRepository = sellerRepository;
    }

    @Override
    public List<Seller> findAll() {
        log.info("Listando Vendedores");
        return sellerRepository.findAll();
    }

    @Override
    public Optional<Seller> findById(Long id) {
        log.info("Buscando Vendedor por ID");
        return sellerRepository.findById(id);
    }

    @Override
    public Seller save(Seller seller) {
        log.info("Guardando vendedor: " + seller.toString());
        seller.setState("A");  // Estado activo
        return sellerRepository.save(seller);
    }

    @Override
    public Seller update(Seller seller) {
        log.info("Actualizando vendedor: " + seller.toString());
        seller.setState("A");  // Estado activo
        return sellerRepository.save(seller);
    }

    @Override
    public void delete(Seller seller) {
        // Cambiar el estado del vendedor a "I" (Inactivo) en lugar de eliminarlo
        seller.setState("I");
        sellerRepository.save(seller); // Guardamos el vendedor con el estado actualizado
    }
}
```
y en la **TERMINAL** colocaras ---> *git add .* y despues colocas

---> **git commit -m "fix: elimination method and list x ID"**

Debe verse asi 

![Captura de pantalla 2025-05-22 a las 4 48 22 a  m](https://github.com/user-attachments/assets/e308d891-9994-4fe6-af42-ebb4e3dd8cf9)

Ahora tendras que volver nuevamente a la carpeta main 

    **SRC**
    └── **main**

Y dirigirte a la carpeta llamada **resources** 

# SCHEMA.SQL

en el archivo **schema.sql** mejoramos tu tabla **seller**

```sql
CREATE TABLE seller (
    id INT IDENTITY(1,1),
    name VARCHAR(100),
    last_name VARCHAR(100),
    dni CHAR(8),
    email VARCHAR(50),
    phone CHAR(9),
    state CHAR(1),
    CONSTRAINT pk_seller PRIMARY KEY (id),

    -- El DNI, CORREO y TELEFONO deben ser único
    CONSTRAINT uq_seller_dni UNIQUE (dni),
    CONSTRAINT uq_seller_email UNIQUE (email),
    CONSTRAINT uq_seller_phone UNIQUE (phone),

    -- DNI y TELEFONO solo deben contener números
    CONSTRAINT chk_dni_numeric CHECK (dni NOT LIKE '%[^0-9]%'),
    CONSTRAINT chk_phone_valid CHECK (phone NOT LIKE '%[^0-9]%' AND LEN(phone) = 9),

    -- El correo electrónico no debe contener espacios
    CONSTRAINT chk_email_format CHECK (
        email LIKE '_%@_%._%' AND
        CHARINDEX(' ', email) = 0
    ),
);
```
y en la **TERMINAL** colocaras ---> *git add .* y despues colocas

---> **git commit -m "feat: restrictions for the seller table"**

## Ahora sube tus cambios a la rama develop

### Te toca a ti ahora yo voy a dormir 
si todo sale mal es culpa de chatGPT xdddd
