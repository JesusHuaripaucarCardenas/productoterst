# **`APLICANDO LOS CONVENTIONAL COMMITS`**

*Sigue estos pasos para sacar 20 xdddd*

## Tu solo sigue los pasos

![image](https://github.com/user-attachments/assets/37dca32b-c177-42c9-9e5f-eb3357f41460)


## **Primero creamos la rama feature**

Crea un codespace nuevo y en la terminal coloca 

### **git checkout -b feature/sp3_u3_products**

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

### **Dentro de la carpeta model** crea un archivo nuevo llamado **Products.java** 

y dentro de el colocaras 

```java
package pe.edu.vallegrande.project.model;

import jakarta.persistence.*;
import lombok.Data;

import java.time.LocalDateTime;

@Entity
@Data
@Table(name = "products")
public class Products {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;

    @Column(name = "selection_quantity")
    private int selectionQuantity;

    @Column(name = "kl_quantity")
    private int klQuantity;

    @Column(name = "output_log")
    private LocalDateTime outputLog;

    @ManyToOne
    @JoinColumn(name = "products_detail_id")
    private ProductsDetail productsDetail;
}
```

y en la **TERMINAL** colocaras ---> *git add .* y despues colocas

---> *git commit -m "feat: Entity and functionality of the product table"*



# REPOSITORY

luego **Dentro de la carpeta repository** crea un archivo nuevo llamado **Products.java** 

y dentro de el colocaras

```java
package pe.edu.vallegrande.project.repository;

import pe.edu.vallegrande.project.model.Products;
import org.springframework.data.jpa.repository.JpaRepository;

public interface ProductsRepository extends JpaRepository<Products, Long> {
}
```

y en la **TERMINAL** colocaras ---> *git add .* y despues colocas

---> *git commit -m "feat: Added a CRUD interface for products"*

# REST

luego **Dentro de la carpeta rest** crea un archivo nuevo llamado **ProductsRest.java** 

y dentro de el colocaras

```java
package pe.edu.vallegrande.project.rest;

import pe.edu.vallegrande.project.model.Products;
import pe.edu.vallegrande.project.service.ProductsService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;

import java.util.List;
import java.util.Optional;

@CrossOrigin(origins = "*")
@RestController
@RequestMapping("/v1/api/products")
public class ProductsRest {

    private final ProductsService productsService;

    @Autowired
    public ProductsRest(ProductsService productsService) {
        this.productsService = productsService;
    }

    @GetMapping
    public List<Products> findAll() {
        return productsService.findAll();
    }

    @GetMapping("/{id}")
    public Optional<Products> findById(@PathVariable Long id) {
        return productsService.findById(id);
    }
}
```

y en la TERMINAL colocaras ---> git add . y despues colocas

---> git commit -m "feat: Create an endpoint or controller for the product table"

# SERVICE

luego **Dentro de la carpeta service** crea un archivo nuevo llamado **ProductsService.java** 

y dentro de el colocaras

```java
package pe.edu.vallegrande.project.service;

import pe.edu.vallegrande.project.model.Products;

import java.util.List;
import java.util.Optional;

public interface ProductsService {

    List<Products> findAll();
    Optional<Products> findById(Long id);
}
```

y en la **TERMINAL** colocaras ---> *git add .* y despues colocas

---> **git commit -m "feat: Basic service operations for the product entity"**

# IMPL

ahora dentro de la carpeta service veras otra carpeta llamada **impl** **Dentro de ella** crea un archivo nuevo llamado **ProductsServiceImpl.java** 

y dentro de el colocaras

```java
package pe.edu.vallegrande.project.service;

import pe.edu.vallegrande.project.model.Products;

import java.util.List;
import java.util.Optional;

public interface ProductsService {

    List<Products> findAll();
    Optional<Products> findById(Long id);
}
```
y en la **TERMINAL** colocaras ---> *git add .* y despues colocas

---> **git commit -m "feat: Implementing Product with CRUD functionality"**

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

en el archivo **schema.sql** agregaras tu tabla **product**

```sql
-- Tabla: products
CREATE TABLE products (
    id INT IDENTITY(1,1) NOT NULL,
    name VARCHAR(100) NOT NULL,
    selection_quantity INT NOT NULL,
    kl_quantity INT NOT NULL,
    output_log DATETIME NOT NULL,
    products_detail_id INT NOT NULL,
    CONSTRAINT pk_products PRIMARY KEY (id)
);
```
y en la **TERMINAL** colocaras ---> *git add .* y despues colocas

---> **git commit -m "feat: product table for data registration"**

# DATA.SQL

luego en el archivo **data.sql** agregaras los datos de tu tabla

```sql
INSERT INTO products (name, selection_quantity, kl_quantity, output_log, products_detail_id) VALUES
('Manzana Fuji', 80, 40, '2024-05-01 10:00:00', 1),
('Plátano de Isla', 70, 35, '2024-05-02 11:30:00', 2);
```
y en la **TERMINAL** colocaras ---> *git add .* y despues colocas

---> **git commit -m "feat: Insert initial data into the product table"**

