# Uso de componentes

En este ejemplo se usará el componente **RecipeViewModel** desde el código C# por debajo de una página.

## 1. Generar un objeto

Antes de todo se debe importar la carpeta que contiene el componente, en este caso es la carpeta **ViewModels** así que se haría de escribiendo al principio del código fuente lo siguiente:

~~~ C#
using EasyCooking.ViewModels;
~~~

La mayoría de componentes permite generar objetos de dos formas: 
- Sin datos, lo que genera la plantilla por defecto.
- Con datos, lo que genera un componente a base de los mismos.

### Objeto sin datos

Para generar la plantilla por defecto basta con hacerlo de la siguiente forma:

~~~ C#
RecipeViewModel objRecipe = new RecipeViewModel();
~~~

Este ejemplo genera un objeto con la plantilla por defecto de un componente de receta.

### Objeto con datos

Para generar un objeto con datos hay que pasarle esos datos como argumentos, para una instancia de `RecipeViewModel` se hace de  la siguiente forma:

~~~ C#
// Generando datos de la receta.
Recipe recipeData = new Recipe(425, "Nacatamal", "c:\\Folder\\img.png", 3, new List<string>(), new List<string>(), "Info...");

// Generando objeto visual.
RecipeViewModel recipe = new RecipeViewModel(recipeData);
~~~

En este caso se genera el componente de receta con los datos del objeto `recipeData`.

## 2. Manejar eventos

Los componentes suelen emitir eventos que se producen en la ejecución del programa, en este caso se manejará el evento **clic** de un `RecipeViewModel`.

Entonces, suponiendo que se desea reaccionar a cada clic que se produce en un componente de receta se debe crear un método (función vacía) siguiendo el ejemplo:

~~~ C#
void OnRecipeClicked(object sender, EventArgs e)
{
    Console.WriteLine("Se ha hecho clic en una receta");
}
~~~

Posteriormente se debe conectar ese método con el clic del objeto, generalmente existen dos formas:

- **Al crear el objeto (recomendada).**

~~~ C#
RecipeViewModel recipe1 = new RecipeViewModel(recipeData, OnRecipeClicked);
~~~

- **Mediante el atributo (recomendable solo cuando se ha generado un objeto sin datos).**

~~~ C#
RecipeViewModel recipe2 = new RecipeViewModel();
recipe2.ClickHandler = OnRecipeClicked;
~~~

Esto haría que al momento de dar un clic se ejecute el método `OnRecipeClicked` asignado.

## Próximo

- [Uso de componentes en listas](./use_list.md)