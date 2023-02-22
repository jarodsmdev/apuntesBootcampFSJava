# M4-ABPRO-2

---

    package m4_abpro_2;

    import java.util.Scanner;
    import java.util.ArrayList;
    //import java.util.Arrays;

    public class ABPRO2 {

        public static void main(String[] args) {
            // TODO Auto-generated method stub

    
    Scanner scanner = new Scanner(System.in);
    
            //Variable global
            String capturador = "";
            int contador = 0;
            int diaSemana = 0;
            String capacitacion [] = new String [10];
            String mensajes [] = new String [10];
            ArrayList <String> asistentes = new ArrayList<String>();
    
            System.out.println("*CREAR CAPACITACION*");
    
    
            //CAPACITACION DIA
            do {
                System.out.println("Ingrese día de la semana [1-7]");
                capturador = scanner.nextLine().trim();
                if(isNumeric(capturador)== true) {
                    diaSemana = Integer.parseInt(capturador);
                }else if(capturador.length()==0){
                    System.out.println("Debe ingresar una opción [1-7]");
                }else {
                    System.out.println("Favor ingrese sólo valores Numéricos de 1 al 7");
                }
    
                if(diaSemana == 1) {
                    capacitacion[0] = "Lunes";
    
                }else if(diaSemana == 2) {
                    capacitacion[0] = "Martes";
                }else if(diaSemana == 3) {
                    capacitacion[0] = "Miércoles";
                }else if(diaSemana == 4) {
                    capacitacion[0] = "Jueves";
                }else if(diaSemana == 5) {
                    capacitacion[0] = "Viérnes";
                }else if(diaSemana == 6) {
                    capacitacion[0] = "Sábado";
                }else if(diaSemana == 7) {
                    capacitacion[0] = "Domingo";
                }else {
                    //System.out.println("Valor fuera de rango");
                }
                    mensajes[0] = "El día será: ";
    
            }while(capturador.length() == 0 || isNumeric(capturador)==false || (Integer.parseInt(capturador) <1 || Integer.parseInt(capturador) >7));
    
            //CAPACITACION HORA
            do {
            
                System.out.println("¿Cuál es la hora? (HH:MM)");
                capturador = scanner.nextLine().trim();

                if(capturador.length() == 0) {
                    System.out.println("[ERROR] No puede estar vacío.");
                }
                if (capturador.matches("^([0-1][0-9]|2[0-3]):[0-5][0-9]$")){
                    mensajes[1] = "La hora está definida a las : ";
                    capacitacion[1] = capturador;
                }else {
                    System.out.println("[ERROR] Hora ingresada NO es válida");
                }
            }while(capturador.length() == 0 || !capturador.matches("^([0-1][0-9]|2[0-3]):[0-5][0-9]$"));
    
            //CAPACITACION LUGAR
            do {
                System.out.println("¿En qué lugar se hara la capacitación?");
                capturador = scanner.nextLine().trim();
                if (capturador.length() == 0) {
                    System.out.println("[ERROR]No puede estar vacío.");
                }else {
                    mensajes[2] = "El lugar : ";
                    capacitacion[2] = capturador;
                }
            }while(capturador.length() == 0);
    
            //CAPACITACION DURACION
            do {
                System.out.println("Ingrese la duración en minutos: ");
                capturador = scanner.nextLine().trim();
                if(capturador.length() == 0) {
                    System.out.println("[ERROR]No puede estar vacío");
                }
                if (isNumeric(capturador) == true) {
                    mensajes[3] = "La capacitación durará ";
                    capacitacion[3] = capturador;
                }else {
                    System.out.println("[ERROR] Sólo valores Numéricos");
                }
    
            }while(capturador.length() == 0 || isNumeric(capturador) == false);
    
            //CAPACITACION CANTIDAD ASISTENTES
    
            do {
                System.out.println("Ingrese el numero de asistentes: ");
                capturador = scanner.nextLine().trim();
                if(capturador.length() == 0) {
                    System.out.println("[ERROR] No puede estar vacío");
                }
                if (isNumeric(capturador) == true && Integer.parseInt(capturador) != 0) {
                    mensajes[4] = "Asistentes son: ";
                    capacitacion[4] = capturador;
                } else {
                    System.out.println("[ERROR] Sólo valores Numéricos");
                }
            }while(capturador.length() == 0 || isNumeric(capturador) == false || Integer.parseInt(capturador) <= 0);
    
    
            System.out.println("**INGRESE DATOS DEL CLIENTE**");
    
            //Cliente RUT 
    
            do{
                System.out.println("Ingrese RUT Cliente:");
                capturador = scanner.nextLine().trim();
                if(capturador.length() == 0) {
                    System.out.println("[ERROR] Debe ingresar RUT de la empresa");
                }else if(capturador.length() > 9) {
                    System.out.println("[ERROR] Debe ingresar un RUT válido");
                }else if(isNumeric(capturador) == false){
                    System.out.println("[ERROR] Favor digite sólo números sin digito verificador");
                }else {
                    mensajes[5] = "RUT EMPRESA: ";
                    capacitacion[5] = capturador;  //GUARDA EL DATO DE CAPTURADOR
                }

            }while(capturador.length() == 0 || capturador.length() >9 || isNumeric(capturador)==false);
    
            //Cliente Nombre

            do {
                System.out.println("Ingrese Nombre del cliente:");
                capturador = scanner.nextLine().trim();
                if(capturador.length()==0){
                    System.out.println("[ERROR] Debe ingresar Nombre del Cliente");
                } else {
                    mensajes[6] = "Nombre Empresa: ";
                    capacitacion[6] = capturador;
                }

            }while(capturador.length() == 0);

           //Cliente Dirección

            do {
                System.out.println("Ingrese Dirección: ");
                capturador = scanner.nextLine().trim();
                if(capturador.length()==0){
                    System.out.println("[ERROR] Debe ingresar Dirección");
                } else {
                    mensajes[7] = "Dirección Empresa: ";
                    capacitacion[7] = capturador;
                }
            }while(capturador.length() == 0);

          //Cliente Comuna

            do {
                System.out.println("Ingrese Comuna: ");
                capturador = scanner.nextLine().trim();
                if(capturador.length()==0){
                    System.out.println("[ERROR] Debe ingresar Comuna");
                } else {
                    mensajes[8] = "Comuna empresa: ";
                    capacitacion[8] = capturador;
                }
            }while(capturador.length() == 0);

          //Cliente Telefono

            do {
                System.out.println("Ingrese Teléfono: ");
                capturador = scanner.nextLine().trim();
                if(capturador.length()==0){
                    System.out.println("[ERROR] Debe ingresar Teléfono");
                } else {
                    mensajes [9] = "Telefono empresa: ";
                    capacitacion[9] = capturador;
                }
            }while(capturador.length() == 0);     





            // INGRESE ASISTENTES
            contador = 1;
            for (int i = 0; i < Integer.parseInt(capacitacion[4]) ; i++) {
                // INGRESO NOMBRE
                do {
                    System.out.println("Ingrese nombre de asistente [#" + contador + "]: ");
                    capturador = scanner.nextLine().trim();
                    if (capturador.length() == 0) { 
                        System.out.println("[ERROR] Debe ingresar el nombre de asistente");
                    } else {
                        asistentes.add(capturador);
                    }

                }while(capturador.length() == 0);


                //INGRESO EDAD
                do {
                    System.out.println("Ingrese edad del asistente: [#" + contador + "]");
                    capturador = scanner.nextLine().trim();
                    if (capturador.length() == 0) {
                        System.out.println("[ERROR] No puede estar vacío"); 
                    }else if(isNumeric(capturador) == false){
                        System.out.println("[ERROR] Favor digite sólo números");
                    }else if (Integer.parseInt(capturador)<0){ 
                        System.out.println("[ERROR] La edad debe ser mayor a 0");   
                    } else{
                        asistentes.add(capturador);
                    }
                }while(capturador.length() == 0 || isNumeric(capturador) == false);

            contador++; //INCREMENTA EN UNO EL CONTADOR DE ASISTENTES
            }

            // MENSAJE DATOS CAPACITACIÓN





            for (int i = 0; i < capacitacion.length; i++) {
                System.out.print(mensajes[i]);
                System.out.println(capacitacion[i]);
            }


            // RANGO DE EDADES

            int bajo25 = 0;
            int rango26a35 = 0;
            int sobre35 = 0;
            int edad;

            for (int i = 0; i <= asistentes.size(); i++) {
            
                if (i%2 != 0) {
                    edad = Integer.parseInt(asistentes.get(i));
                    if (edad <= 25) {
                        bajo25++;
                    } else if (edad >= 26 && edad <= 35) {
                        rango26a35++;
                    } else {
                        sobre35++;
                    }
                }

            }

            System.out.println("");
            System.out.println("**RESUMEN EDADES**");


            System.out.println("Cantidad de personas menores de 25 años: " + bajo25);
            System.out.println("Cantidad de personas entre 26 y 35 años: " + rango26a35);
            System.out.println("Cantidad de personas mayores a 35 años: " + sobre35);
            
            //CIERRA EL OBJETO scanner
            scanner.close();
        }
    
        //FUNCIÓN AUXILIAR PARA VALIDAR VALORES NUMERICOS
        private static boolean isNumeric(String cadena){
            try{
                Integer.parseInt(cadena);
                return true;
            }catch(NumberFormatException nfe){
                return false;
            }
        }
    }
