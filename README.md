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
