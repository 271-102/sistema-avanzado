# sistema-avanzado
casandra
def menu():
    inventario = Inventario()
    inventario.cargar_archivo("inventario.dat")
    
    while True:
        print("\n--- MENÚ INVENTARIO ---")
        print("1. Agregar producto")
        print("2. Eliminar producto")
        print("3. Actualizar producto")
        print("4. Buscar producto")
        print("5. Mostrar todos los productos")
        print("6. Guardar y salir")
        opcion = input("Seleccione una opción: ")

        if opcion == "1":
            id = input("ID: ")
            nombre = input("Nombre: ")
            cantidad = int(input("Cantidad: "))
            precio = float(input("Precio: "))
            producto = Producto(id, nombre, cantidad, precio)
            inventario.agregar_producto(producto)
        elif opcion == "2":
            id = input("ID del producto a eliminar: ")
            inventario.eliminar_producto(id)
        elif opcion == "3":
            id = input("ID del producto a actualizar: ")
            cantidad = input("Nueva cantidad (dejar vacío para no cambiar): ")
            precio = input("Nuevo precio (dejar vacío para no cambiar): ")
            inventario.actualizar_producto(id, int(cantidad) if cantidad else None, float(precio) if precio else None)
        elif opcion == "4":
            nombre = input("Nombre del producto a buscar: ")
            resultados = inventario.buscar_producto(nombre)
            for p in resultados:
                print(p)
        elif opcion == "5":
            inventario.mostrar_productos()
        elif opcion == "6":
            inventario.guardar_archivo("inventario.dat")
            print("Inventario guardado. ¡Hasta luego!")
            break
        else:
            print("Opción no válida. Intente de nuevo.")

if __name__ == "__main__":
    menu()
