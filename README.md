# Trabajo-de-Consulta-2
// Función para calcular la integral usando el método de Simpson
def integracion(f: Double => Double, a: Double, b: Double): Double = {
  val h = (b - a) / 2
  (b - a) * (f(a) + 4 * f(a + h) + f(b)) / 6
}

// Función para calcular el error
def calcularError(valorEsperado: Double, valorObtenido: Double): Double = {
  Math.abs(valorEsperado - valorObtenido)
}

// Función principal para ejecutar las integraciones
object Main extends App {
  val funciones = List(
    (x: Double) => -x * x + 8 * x - 12,
    (x: Double) => 3 * x * x,           
    (x: Double) => x + 2 * x * x - x * x * x + 5 * x * x * x * x, 
    (x: Double) => (2 * x + 1) / (x * x + x), 
    (x: Double) => Math.exp(x),         
    (x: Double) => 1 / Math.sqrt(x - 1), 
    (x: Double) => 1 / (1 + x * x)      
  )

  val valoresEsperados = List(7.33, 8.0, 3.333, 1.09861, 1.71828, 0.828427, 0.785398)
  for (i <- funciones.indices) {
    val resultado = integracion(funciones(i), 3 + i * 2, 5 + i * 2)
    val error = calcularError(valoresEsperados(i), resultado)
    println(s"Integral ${i + 1}: Valor obtenido = $resultado, Error = $error")
  }
}
