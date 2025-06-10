# Cambios-moto
Para llevar el seguimiento de cambios y mantenimiento a la motocicleta o automóvil desde su dispositivo.

Para preguntas comucarse vía WhatsApp al https://wa.me/573025120941

## paso 1

descargar de la playstore PyDroid 3 (pyto en iPhone) y apcete todos los permisos

## paso 2

copiar y pegar el siguiente código Pydroid

```python
mantenimiento_moto = {
    # Cambios de Fluidos y Filtros
    "cambio_aceite_motor_km": [7, 3000],
    "cambio_aceite_sintetico_km": [7, 6000],
    "cambio_filtro_aceite_km": [7, 7000],
    "cambio_filtro_aire_km": [7, 8500],
    "cambio_liquido_frenos_km": [7, 18000],
    "cambio_liquido_refrigerante_km": [7, 27000],
    # Sistema de Transmisión
    "limpieza_lubricacion_cadena_km": [7, 500],
    "ajuste_tension_cadena_km": [7, 1200],
    "cambio_kit_arrastre_km": [7, 23000],
    # Frenos
    "cambio_pastillas_freno_km": [7, 9500],
    "revision_discos_freno_km": [7, 14000],
    "sangrado_liquido_frenos_km": [7, 19500],
    # Sistema Eléctrico
    "cambio_bujias_km": [7, 10200],
    "revision_bateria_km": [7, 5400],
    "revision_sistema_electrico_km": [7, 5600],
    # Neumáticos y Suspensión
    "revision_presion_neumaticos_km": [7, 1000],
    "cambio_neumaticos_km": [7, 15500],
    "revision_amortiguadores_km": [7, 20500],
    # Motor y Partes Mecánicas
    "ajuste_valvulas_km": [7, 15800],
    "cambio_correa_distribucion_km": [7, 42000],
    "limpieza_carburador_km": [7, 10900],
    # Revisiones Generales
    "revision_general_km": [7, 5000],
}

def proximos_mantenimientos(kilometraje_actual):
    mantenimientos_proximos = []

    for nombre, valores in mantenimiento_moto.items():
        ultimo_cambio, intervalo_km = valores
        
        # Calcula el próximo cambio en base al último realizado
        if kilometraje_actual < ultimo_cambio:
            proximo_km = ultimo_cambio
        else:
            proximo_km = ((kilometraje_actual - ultimo_cambio) // intervalo_km + 1) * intervalo_km + ultimo_cambio
        
        for repeticion in range(3):  # Próximas 3 ocurrencias de este mantenimiento
            km = proximo_km + (repeticion * intervalo_km)
            mantenimientos_proximos.append((nombre, km))

    # Ordenar por kilometraje y filtrar únicos (por si hay duplicados cercanos)
    mantenimientos_proximos = sorted(list(set(mantenimientos_proximos)), key=lambda x: x[1])

    # Tomar los 5 más cercanos
    proximos_5 = mantenimientos_proximos[:15]

    # Mostrar resultados
    print(f"\nPróximos 15 mantenimientos (a partir de {kilometraje_actual} km) serán:")
    print("-" * 60)
    for nombre, km in proximos_5:
        nombre_formateado = nombre.replace("_", " ").replace(" km", "").title()
        print(f"{km} km {nombre_formateado:<30} → (faltan {km - kilometraje_actual} km)")
    print("-" * 60)

# Ejemplo de uso
try:
    kilometraje_actual = int(input("Ingrese el kilometraje actual de su vehículo (km): "))
    kilometraje_actual -= 100
    proximos_mantenimientos(kilometraje_actual)
except ValueError:
    print("Error: Ingrese un número válido y no letras")
```

## paso3

Ejecutar el archivo con el círculo amarillo

## paso 4

El programa se verá algo así:

```
Ingrese el kilometraje actual de su vehículo (km):






```
Si usted ingresa '8888' como valor en el kilometraje que le piden le tiene que salirle lo siguiente
```
Ingrese el kilometraje actual de su vehículo (km): 8888

Próximos 15 mantenimientos (a partir de 8788 km) serán:
------------------------------------------------------------
9007 km Revision Presion Neumaticos    → (faltan 219 km)
9007 km Limpieza Lubricacion Cadena    → (faltan 219 km)
9007 km Cambio Aceite Motor            → (faltan 219 km)
9507 km Cambio Pastillas Freno         → (faltan 719 km)
9507 km Limpieza Lubricacion Cadena    → (faltan 719 km)
9607 km Ajuste Tension Cadena          → (faltan 819 km)
10007 km Revision Presion Neumaticos    → (faltan 1219 km)
10007 km Limpieza Lubricacion Cadena    → (faltan 1219 km)
10007 km Revision General               → (faltan 1219 km)
10207 km Cambio Bujias                  → (faltan 1419 km)
10807 km Ajuste Tension Cadena          → (faltan 2019 km)
10807 km Revision Bateria               → (faltan 2019 km)
10907 km Limpieza Carburador            → (faltan 2119 km)
11007 km Revision Presion Neumaticos    → (faltan 2219 km)
11207 km Revision Sistema Electrico     → (faltan 2419 km)
------------------------------------------------------------

[Program finished] 
```
para volver a consultar oprima el icono de flecha izquierda y ya después vuelver a oprima el círculo amarillo
