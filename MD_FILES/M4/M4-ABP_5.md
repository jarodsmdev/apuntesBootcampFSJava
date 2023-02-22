# M4-ABP_5

---

    package m4ABP5;
    import java.util.Scanner;

    public class ABP5 {

    public static void main(String[] args) {
        // TODO Auto-generated method stub
        System.out.println("**CALCULADORA MALOTA >:/**");
    
        String capturador = "";
        Scanner scanner = new Scanner(System.in);
        int primerNumero = 0;
        int segundoNumero = 0;
        String operador = "";
        String regEx = "^[\\+\\-\\*/%]$";

    
        //INGRESO Y VALIDACIÓN DEL PRIMER NÚMERO
        do {
            System.out.print("Ingrese primer número: ");
            capturador = scanner.nextLine().trim();
            if(capturador.length() == 0) {
                System.out.println("[ERROR] No puede estar vacío, favor ingrese un número");
            }else if(isNumeric(capturador)) {
                //NUMERO INGRESADO
                primerNumero = Integer.parseInt(capturador);
            }else {
                //TEXTO INGRESADO
                System.out.println("[ERROR] No ha ingresado un número");
            }
        }while(capturador.length() == 0 || isNumeric(capturador) == false);
    
    
    
        //INGRESO Y VALIDACION DE CARACTERES DE OPERACION
        do {
            System.out.println("Favor ingrese el caracter correspondiente a la operación que desee realizar");
            System.out.println("+, -, * , /, %");
            capturador = scanner.nextLine();
            if(!capturador.matches(regEx)) {
                System.out.println("[ERROR] Caracter ingresado no corresponde a los permitidos");
            }else {
                operador = capturador;
            }
        }while(!capturador.matches(regEx)); 
    
        //INGRESO Y VALIDACIÓN SEGUNDO NÚMERO
        do {
            System.out.print("Ingrese segundo número: ");
            capturador = scanner.nextLine().trim();
            if(capturador.length() == 0) {
                System.out.println("[ERROR] No puede estar vacío, favor ingrese un número");
            }else if(isNumeric(capturador)) {
                //NUMERO INGRESADO
                segundoNumero = Integer.parseInt(capturador);
            }else {
                //TEXT INGRESADO
                System.out.println("[ERROR] No ha ingresado un número");
            }
        }while(capturador.length() == 0 || isNumeric(capturador) == false);
    
        //RESOLUCIÓN
        double resultado;
        switch(operador) {
        case "+":
            resultado = primerNumero + segundoNumero;
            System.out.println("La suma entre " + primerNumero + " y " + segundoNumero + " es " + resultado);
            break;
        case "-":
            resultado = primerNumero - segundoNumero;
            System.out.println("La resta entre " + primerNumero + " y " + segundoNumero + " es " + resultado);
            break;
        case "/":
            if(segundoNumero == 0) {
                System.out.println("No es posible dividir por cero");
            }else {
                resultado = primerNumero / segundoNumero;
                System.out.println("La división entre " + primerNumero + " y " + segundoNumero + " es " + resultado);
            }
            break;
        case "*":
            resultado = primerNumero * segundoNumero;
            System.out.println("La multiplicación entre " + primerNumero + " y " + segundoNumero + " es " + resultado);
            break;
        case "%":
            resultado = primerNumero % segundoNumero;
            System.out.println("El residudo de la división entre " + primerNumero + " y " + segundoNumero + " es " + resultado);
            break;
        default:
            System.out.println("Operador inválido.");
        }

    
    }

    //FUNCIÓN PARA VALIDAR NÚMEROS
    private static boolean isNumeric(String cadena){
        try{
            Integer.parseInt(cadena);
            return true;
        }catch(NumberFormatException nfe){
            return false;
        }
    }
    }
