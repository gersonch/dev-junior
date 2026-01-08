# Tarea Dev Junior - Ruuf

## 🎯 Objetivo

El objetivo de este ejercicio es poder entender tus habilidades como programador/a, la forma en que planteas un problema, cómo los resuelves y finalmente cómo comunicas tu forma de razonar y resultados.

## 🛠️ Problema

El problema a resolver consiste en encontrar la máxima cantidad de rectángulos de dimensiones "a" y "b" (paneles solares) que caben dentro de un rectángulo de dimensiones "x" e "y" (techo).

## ✅ Solución

### 📐 Cálculo de áreas

Primero realicé el calculo de area para los dos rectangulos

```typescript
const roofArea = roofWidth * roofHeight;
const panelArea = panelWidth * panelHeight;
```

y dividi el area de "roof" por el area de "panel". Esto funciono para algunos test pero me faltaba realizar validaciones importantes ya que me hacia la division sin tener en cuenta si realmente un panel entraba en el rectangulo mas grande.

### 🔍 Validación básica

Entonces hice un if simple.

```typescript
if (panelWidth > roofWidth || panelHeight > roofHeight) return 0;
```

y solo con esto ya paso todos los test.

### 🔄 Rotación

pero aun asi no me conforme ya que hay casos en la vida real en las que no funcionaria ya que nosotros podriamos rotar un rectangulo y cabria perfectamente. Asi que agregue un test extra al ejercicio para comprobar.

```json
{
  "panelW": 2,
  "panelH": 5,
  "roofW": 6,
  "roofH": 3,
  "expected": 1
}
```

en este caso me devuelve 0 cuando deberia devolverme 1. Esto es por que el alto del panel es mas grande que el alto del roof pero si lo rotamos cabria perfectamente. Entonces para esto deberia agregar unas validaciones extra.

```typescript
const fitsOriginal = panelWidth <= roofWidth && panelHeight <= roofHeight;
const fitsRotated = panelHeight <= roofWidth && panelWidth <= roofHeight;

if (!fitsOriginal && !fitsRotated) {
  return 0;
}
```

esto me serviria para saber que si no cabe en la posicion original talvez pueda caber en la otra posición.
