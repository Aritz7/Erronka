---
layout: page
title: Datu-Baseak
---
# Datu baseak - Proiektuaren Dokumentazioa

## 1. Brainstorming eta ideia orokorra

### 1.1. Brainstorming 
Para empezar con el apartado de base de datos, hemos optado por hacer un brainstorming para aportar la mayor cantidad de ideas para el proyecto. Con este metodo hemos conseguido aportar la mayoria de entidades y de atributos que aparecen en la base de datos final. 
    
### 1.2. Ideia orokorra 
Una vez con la fase de brainstorming completada, nos dispusimos a enlazar todo lo optenido de la forma mas optima posible y a la vez adaptandola a nuestra idea de pagina web. En este paso diseñamos el primer esquema para que fuese lo mas comprensible y a la vez facil de crear posible. Con esto hecho, al crear nuestra E/R esquema nos facilitara el proceso.



![Planifikazioaren irudia 1](img/DB1.jpg)


---

## 2. E/R esquema

### 2.1. Diseño definitivo E/R esquema
Con el trabajo muy facilitado gracias al anterior paso, nuestro trabajo se redujo a tres sencillos pasos. El primer paso fue reducir el esquema para adaptarlo a nuestras necesidades reales. Aqui descartamos todo el apartado de la produccion y la entidad "Komentario" para que el diseño final no se extendiese en exceso. El segundo paso fue dibujar el esquema en papel con los atributos figurando ya en el esquema, colocar las cardinales y usar el codigo preciso para todo lo anterior. El tercer y ultimo paso fue corregir distintos fallos que encontramos a lo largo del proceso para tener el boceto definitivo.



![Planifikazioaren irudia 1](img/DB2.jpg)


---

### 2.2. Digitalizar el E/R esquema
Con un boceto ya definido, decidimos crear una version digitalizada para pulir aun mas nuestro trabajo ademas de corregir otros fallos que hemos ido encontrando. Para esta tarea decidimos usar la app Visio. En ella la tarea solo fue ir pasando lo que habia en el papel, dibujado a lapiz, a la app usando sus diferentes figuras y conexiones. Para que el diseño quedara aun mas claro, usamos diferentes colores para cada elemento (por ejemplo: Berde-relaciones)



![Planifikazioaren irudia 1](img/DB4.png)


---

### 2.3. Explanation
**Data base explanation:**

We want to store different data for a company that provides a web platform similar to Netflix.

To fulfill this request, we begin with a user entity, through which we will collect the following data: Name, ID, Password, date of creation of the account, date of birth, and email address.

Also, each user will acquire a plan to access our platform. The plans can be one of these 4: Individual basic, individual premium, family basic, and family premium. To keep this data correctly, we decided to create two different entities, “subscription” and “plan”. By making this division, we can identify which users are on the same family plan. On the plan entity, we will keep this information: Name, ID, Price per month, and description (explaining if the plan has ads…). On the subscription entity, we will keep: ID, Payment method, Duration, start date, renewal type (Automatic or manual). A user must have one subscription, and each subscription will have between 1 and 5 users (family plans maximum capacity of users will be 5). Each subscription is linked to a plan, and a plan can have multiple subscriptions.

Additionally, each user will have a role, and a role can belong to multiple users. The web will only have 2 different roles, adults and kids. The role entity will keep the name, ID, and Access type (if it has complete access or access to under 18 content only). This entity is linked to a content entity. A role can allow multiple contents, and a content is allowed by 1 or 2 roles (because there are only 2 different roles); therefore, 18+ content will only be seen by adults, and children's content could be watched by kids and adults as well.

The content entity will keep this information: Title, ID, minimum age required to watch, duration, amount of likes, and amount of dislikes. Also, this entity is linked to “user”; a user can watch no content or watch multiple contents, and each individual content can be watched by no users or by multiple users. Also, in the relationship, we will keep the stop marker, the feedback and the timestamp (we will know at what exact point of the content the user stopped watching it the last time).

To continue, we want to store different types of content, so we implemented an ISA relation with complete exclusivity. So, we have 3 sub-entities: film, documentary, and episodes.  Episodes,  will be the only entity that will have anything different, because we want to know each episode from what season/serie is. To do this, we linked to another entity called season/serie, which will keep the ID, and the title. Each episode belongs to a serie/season and each serie/season will have multiple episodes.  

To conclude, we will keep the genre and subgenres of the content. To do this, we created another entity called genre; it will keep the ID and the name, and it will be connected to content. Each content can have multiple genres, and each genre applies to multiple contents. To store the subgenres, we created a recursive relationship. Each genre can have 0 or many subgenres, and each subgenre belongs to only one genre.


---

### 2.3. Teknologia Gaitzaile Digitalak (TGD / THD)
**Plan** : ( IDplan, name, price, description )
**Subscription** : ( IDsubscription, paying method, renew type, duration, date start, IDplan )
**Users** : ( IDuser, Name, password, date of birth, date of creation, email, IDsubscription, IDrol )
**Rol** : ( IDrol, Name, Access type )
**Content** : ( IDcontent, title, minimun age, duration, sumary )
**Film** : ( IDcontent )
**Documental** : ( IDcontent )
**Episodes** : ( IDcontent, IDseason )
**Serie / season** : ( IDseason, title )
**Content + rol** : ( IDrol, IDcontent )
**Content + users** : ( IDusers, IDcontent, time stamp, stop mark, feedback ) <mark><u>IDrol</u></mark>

---

### 2.4. Cloudean Oinarritutako Sistemak (Cloud Computing)
Cloud computing-a Internet bidez eskuragarri dauden baliabide informatikoak (zerbitzariak, biltegiratzea, aplikazioak) urrunetik erabiltzeko eredua da, azpiegitura fisiko lokal baten mende egon gabe.

**Ezaugarriak eta Mailak:**
* **Eredu Tradizionala vs Hodeia:** Eredu tradizionalean datuak eta programak gailu lokalean instalatzen eta gordetzen dira; hodeian, berriz, edozein gailutatik atzitu daitezke Internet bidez, biltegiratze lokala muga izan gabe.
* **Hodei motak:** Publikoa, Pribatua eta Hibridoa.
* **Zerbitzu Ereduak (Kontenedoreak):**
  * **IaaS (Infrastructure as a Service):** Azpiegitura birtuala alokatzea (adib. Azure VM, Amazon EC2).
  * **PaaS (Platform as a Service):** Aplikazioak garatzeko plataforma (adib. Google App Engine).
  * **SaaS (Software as a Service):** Erabiltzeko prest dauden software-aplikazioak (adib. Google Workspace, Microsoft 365).
* **Eboluzioa (Fog / Edge / Mist Computing):** Hodeiko latentzia eta banda-zabalera hobetzeko, prozesamendua datu-iturritik gertuago egiteko garatutako teknologiak.