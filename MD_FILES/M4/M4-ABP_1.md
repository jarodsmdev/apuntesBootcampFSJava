# M4-ABP_1

---

## Requerimiento funcional

Se pide que el algoritmo y pieza de código Java solicite al usuario cada uno de los valores antes mencionados, los almacene en una variable y los despliegue por pantalla. Además, debe realizar la validación que se indica en cada campo y, en caso de que alguna de las validaciones no se haya cumplido, debe retornar un mensaje de error.

    package m4_ABP1;

    import java.util.Scanner;

    public class ciaSeguros {

    public static void main(String[] args) {
        // TODO Auto-generated method stub
    
        // DECLARAR GLOBALES
        String capturaDatos;
        int i;
    
        // Variables
        int RUT;
        String Nombres;
        String Apellidos;
        int Telefono;
        String AFP;
        int SistSalud;
        String Direccion;
        String Comuna;
        int Edad;
    
        // Instanciar la clase Scanner
        Scanner myObj = new Scanner(System.in);
    
    
    
        //Validacion de RUT (solo numeros, no vacío)
        System.out.println("Ingrese RUT:");
        capturaDatos = myObj.nextLine();
        if (isNumeric(capturaDatos)) {
            RUT = Integer.parseInt(capturaDatos);
            if (RUT < 99999999) {
                System.out.println("RUT: " + RUT);
            }else {
                System.out.println("El Rut ingresado es un número muy alto");
            }
        }else {
            System.out.println("Rut ingresado no es válido");
            System.exit(0);
        }
    
        //Validar Nombres Obligatorio
        i = 0;
        do {
            System.out.println("["+ i +"]Ingrese su Nombre: ");
            Nombres = myObj.nextLine().trim();
            i++;
        } while (Nombres.length() == 0);
        System.out.println("Nombre: " + Nombres);

        //Validar Apellidos Obligatorio
        i = 0;
        do {
            System.out.println("["+ i +"]Ingrese su apellido: ");
            Apellidos = myObj.nextLine().trim();
            i++;
        } while (Apellidos.length() == 0);
            System.out.println("Apellido: " + Apellidos);
    
        //Validar Teléfono no más de 15 carácteres
        do {
            System.out.println("Ingrese su número telefónico: ");
            capturaDatos = myObj.nextLine().trim();
            if (isNumeric(capturaDatos)) {
                Telefono = Integer.parseInt(capturaDatos);
                System.out.println("Teléfono: " + Telefono);
            }
    
            } while (capturaDatos.length() > 15);
            if(capturaDatos.length() >15) {
                System.out.println("No más de 15 dígitos");
            }
    
        //validar afp obligatorio
        i = 0;
        do {
            System.out.println("[" + i + "]Ingrese AFP: ");
            capturaDatos = myObj.nextLine().trim();
            i++;
            if (capturaDatos.length()>0) {
                AFP = capturaDatos;
    
                System.out.println("AFP : " + AFP);
            }
        }while(capturaDatos.length()==0);
    
        //Validar Sistema salud 1 o 2
        SistSalud = 0;
        i = 0;
        do {
            System.out.println("[" + i +"]Ingrese Sistema de Salud: ");
            capturaDatos = myObj.nextLine().trim();
    
            if (isNumeric(capturaDatos)) {
                SistSalud = Integer.parseInt(capturaDatos);
    
            }else {
                System.out.println("El valor no es numérico");
            }
    
            i++;
            if (SistSalud == 1 || SistSalud == 2) {
                if(SistSalud == 1) {
                    System.out.println("Sistema de Salud: FONASA");
                }else {
                    System.out.println("Sistema de Salud: Isapre");
                }
            }else {
                System.out.println("Debe seleccionar 1 [Fonasa] o 2 [Isapre]");
    
            }
        }while(SistSalud != 1 && SistSalud != 2);
    
        // Validar direccion no superior a 50 caracteres
        do {
            System.out.println("Ingrese su dirección: ");
            capturaDatos = myObj.nextLine().trim();
            if (capturaDatos.length() > 50) {
                System.out.println("Máximo sólo 50 caracteres");
            }else {
                Direccion = capturaDatos;
            };
    
        }while(capturaDatos.length()>50);
    
        //Validar Comuna obligatorio
        Comuna = "";
        i = 0;
        do {
        System.out.println("["+ i +"]Ingrese su comuna: ");
        capturaDatos = myObj.nextLine().trim();
        if (capturaDatos.length()>0) {
            Comuna = capturaDatos;
        }
        i++;
        }while(capturaDatos.length() == 0);
        System.out.println("Comuna: " + Comuna );
    
        // Validar edad menor a 120
        i=0;
        do {
            System.out.println("["+ i +"]Ingrese su edad: ");
            capturaDatos = myObj.nextLine().trim();
            i++;
            if (isNumeric(capturaDatos)) {
                Edad = Integer.parseInt(capturaDatos);
                if(Edad < 0 || Edad >120) {
                    System.out.println("Edades no válidas, sólo se permite hasta 120 años");
                }
            }else {
                System.out.println("Valor ingresado no válido");
                Edad = 121;
            }
        }while(Edad < 0 || Edad > 120);
        System.out.println("**FIN PROGRAMA**");
    
    
    }
        private static boolean isNumeric(String cadena) {
        try {
            Integer.parseInt(cadena);
            return true;
        }catch (NumberFormatException nfe) {
            return false;
        }
    }
    }
