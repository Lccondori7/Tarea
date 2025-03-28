Condori Machaca Luz Clara

import datetime

class CuentaBancaria:
    def __init__(self, titular, saldo_inicial=0):
        self.titular = titular
        self.saldo = saldo_inicial
        self.movimientos = []  # Lista de tuplas: (fecha, tipo, monto, saldo)

    def depositar(self, monto):
        # Completar lo siguiente: 
        # 1. actualizar saldo 
        self.saldo += monto
        # 2. añadir movimiento de deposito (fecha, tipo, monto, saldo) 
        fecha = datetime.datetime.now()
        self.movimientos.append(( fecha, "Depósito", monto, self.saldo))
         # 3. Mostrar mensaje de depósito exitoso
        print("-" * 100)
        print("  \n                                  DEPOSITO EXITOSO    :)    " )
        print("                                 ------------------")
        print(f"En {fecha} : {self.titular} depositó  {monto} Bs. y su saldo actual es de: (Bs.): {self.saldo}")


    def retirar(self, monto):
        # Completar lo siguiente: 
        # 1. Validar saldo, y si es insuficiente mostrar mensaje
        if monto > self.saldo:
            print("-" * 100)
            print("  \n                                 SALDO INSUFICIENTE  :)    " )
            print("                               ------------------------")
            print(f"{self.titular} no puede retirar Bs.{monto} (CUenta con saldo insuficiente: (Bs.) {self.saldo})")
            return False

         # 2. Actualizar saldo   
        self.saldo -= monto
        
        # 3. Añadir movimiento de retiro (fecha, tipo, monto, saldo) 
        fecha = datetime.datetime.now()
        self.movimientos.append((fecha,"Retiro", monto, self.saldo))
          
        # 4. Mostrar mensaje de retiro exitoso

        print("-" * 100)
        print(" \n                                  RETIRO EXITOSO      :( " )
        print("                               --------------------")

        print(f"En {fecha} : {self.titular} retirò - {monto} Bs. y su saldo actual es de: (Bs.): {self.saldo}")
        print("-" * 100)

              
    def mostrar_saldo(self):
        # Completar lo siguiente: 
        # 1. mostrar mensaje con nombre de titular y su saldo.
        print("-" * 100)
        print("  \n                                DETALLES DEL CLIENTE                                        ")
        print("                                --------------------")
        print(f"\n Titular:     {self.titular}")
        print(f" Saldo actual: (bS.)    {self.saldo}")
        print(f"\n ")

    def mostrar_movimientos(self):
        print(f"\n--- Historial de {self.titular} ---")
        # Completar lo siguiente: 
        # 1. iterar la lista de movimientos y mostar la fecha, tipo el monto y el saldo.


        print("-" * 100)
        print("  FECHA   ", "    TIPO", "    MONTO", "   SALDO")
        for fecha, tipo, monto, saldo in self.movimientos:
          print(f"{fecha.strftime('%d/%m/%Y')} : {tipo} -  {monto} Bs. "  f" {saldo} Bs."
    )
