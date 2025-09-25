# NutriApi
# 🥗 Comparativa de APIs Nutricionales

| 🌐 API                 |  Datos que ofrece                                        | 💲 Costo              | ⏳ Límite gratuito              | ⚙️ Implementación | 📖 Documentación |
|------------------------|------------------------------------------------------------|-----------------------------|--------------------------------|-------------------|-----------------|
| **Nutritionix**        | Alimentos, marcas, restaurantes, recetas, análisis nutric. |  Gratis (10,000 consultas/día no comercial) | 10,000 requests/día            | ⭐⭐⭐⭐☆ Fácil       | ⭐⭐⭐⭐⭐ Completa |
| **CalorieNinjas**      | Nutrición de alimentos/bebidas, recetas, texto → info      |  Gratis con API key        | Limitado ( 50 requests/día en gratuito) | ⭐⭐⭐⭐☆ Fácil       | ⭐⭐⭐⭐☆ Muy buena |
| **USDA FoodData Central** | Datos oficiales de alimentos básicos/procesados           |  100% Gratis               | 1,000 requests/hora por IP     | ⭐⭐⭐☆ Media        | ⭐⭐⭐⭐⭐ Completa  |

# 🥗 Investigación sobre Nutritionix API

## ✅ Justificación de elección

Decidimos elegir **Nutritionix** como la API principal para nuestra investigación porque consideramos que ofrece el mejor equilibrio entre **cantidad de datos, facilidad de uso y documentación accesible**.  

A diferencia de otras opciones, no solo incluye información de **alimentos en general**, sino también de **marcas comerciales**, lo cual ayuda al momento de desarrollar aplicaciones relacionadas con nutrición.  

Cuenta con un **plan gratuito**, permitiendo hasta **10,000 consultas al día para uso no comercial**, lo que es suficiente para proyectos escolares sin necesidad de pagar.  

Por otra parte, su **implementación es sencilla**, ya que trabaja con **peticiones REST** y devuelve la información en **formato JSON**.  

Por último, su **documentación es muy completa y bien organizada**, lo cual facilita mucho la integración.  

---

## 📌 Ejemplos de Solicitudes y Respuestas

### 🔹 Ejemplo 1: Búsqueda por texto natural

**Solicitud (Request):**
```bash
curl -X POST "https://trackapi.nutritionix.com/v2/natural/nutrients" \
  -H "Content-Type: application/json" \
  -H "x-app-id: TU_APP_ID" \
  -H "x-app-key: TU_API_KEY" \
  -d '{
        "query": "2 tacos al pastor and 1 coca cola"
      }'
Respuesta (Response):

{
  "foods": [
    {
      "food_name": "taco",
      "serving_qty": 2,
      "serving_unit": "tacos",
      "nf_calories": 310,
      "nf_total_fat": 12,
      "nf_protein": 20,
      "nf_total_carbohydrate": 28
    },
    {
      "food_name": "coca cola",
      "serving_qty": 1,
      "serving_unit": "can",
      "nf_calories": 140,
      "nf_total_fat": 0,
      "nf_protein": 0,
      "nf_total_carbohydrate": 39
    }
  ]
}


👉 La API reconoce los alimentos dentro del texto y devuelve calorías, grasas, proteínas y carbohidratos.

🔹 Ejemplo 2: Información por ID o UPC

Solicitud (Request):

curl -X GET "https://trackapi.nutritionix.com/v2/search/item?nix_item_id=513fceb475b8dbbc21000fd3" \
  -H "x-app-id: TU_APP_ID" \
  -H "x-app-key: TU_API_KEY"


Respuesta (Response):

{
  "foods": [
    {
      "food_name": "Cheddar Cheese",
      "brand_name": "Generic",
      "serving_qty": 1,
      "serving_unit": "oz",
      "nf_calories": 113,
      "nf_total_fat": 9,
      "nf_protein": 7,
      "nf_total_carbohydrate": 1
    }
  ]
}


👉 Devuelve la información nutricional de un alimento específico (ejemplo: queso cheddar).

🔹 Ejemplo 3: Autocompletar búsqueda

Solicitud (Request):

curl -X GET "https://trackapi.nutritionix.com/v2/search/instant?query=apple" \
  -H "x-app-id: TU_APP_ID" \
  -H "x-app-key: TU_API_KEY"


Respuesta (Response):

{
  "common": [
    { "food_name": "apple", "serving_unit": "medium (3\" dia)", "tag_id": "apple" },
    { "food_name": "apple juice", "serving_unit": "cup", "tag_id": "apple juice" }
  ],
  "branded": [
    { "food_name": "Apple Juice", "brand_name": "Tropicana", "nix_item_id": "12345" }
  ]
}


👉 Devuelve sugerencias de alimentos comunes y de marcas comerciales.

🐍 Ejemplos en Python
Ejemplo 1: Búsqueda por texto natural
import requests

url = "https://trackapi.nutritionix.com/v2/natural/nutrients"

headers = {
    "x-app-id": "TU_APP_ID",
    "x-app-key": "TU_API_KEY",
    "Content-Type": "application/json"
}

body = {
    "query": "2 tacos al pastor and 1 coca cola"
}

response = requests.post(url, headers=headers, json=body)
print(response.json())

Ejemplo 2: Buscar alimento por ID o UPC
import requests

url = "https://trackapi.nutritionix.com/v2/search/item"

params = {
    "nix_item_id": "513fceb475b8dbbc21000fd3"  # ID de ejemplo
}

headers = {
    "x-app-id": "TU_APP_ID",
    "x-app-key": "TU_API_KEY"
}

response = requests.get(url, headers=headers, params=params)
print(response.json())

Ejemplo 3: Autocompletar búsqueda
import requests

url = "https://trackapi.nutritionix.com/v2/search/instant"

params = {
    "query": "apple"
}

headers = {
    "x-app-id": "TU_APP_ID",
    "x-app-key": "TU_API_KEY"
}

response = requests.get(url, headers=headers, params=params)
print(response.json())

