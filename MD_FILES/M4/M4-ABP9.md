# M4-ABP9

---

    package m4ABP9;
    import java.util.ArrayList;
    import java.util.Scanner;
    import java.util.Collections;

    public class M4ABP9 {
    static Scanner scanner = new Scanner(System.in);
    static String capturador = "";
    static int contador = 1;
    static ArrayList<Integer> listaNumeros = new ArrayList<Integer>();

        public static void main(String[] args) {
            // TODO Auto-generated method stub
            ingresoNumeros();
            System.out.println("CÁLCULO DE LA LISTA DE NÚMEROS");
            System.out.println("Promedio: " + calculaPromedio(listaNumeros));
            System.out.println("Número Minimo: " + calculaNumMin(listaNumeros));
            System.out.println("Número Máximo: " + calculaNumMax(listaNumeros));
            System.out.println("");
            //ELIMINA PARES
            eliminaNumPares(listaNumeros);
    
            System.out.println("CÁLCULO DE LA LISTA SIN NÚMEROS PARES");
            System.out.println("Promedio : " + calculaPromedio(listaNumeros));
            System.out.println("Número Mínimo : " + calculaNumMin(listaNumeros));
            System.out.println("Número Máximo : " + calculaNumMax(listaNumeros));
        }
    
        //FUNCIÓN QUE VALIDA INGRESO DE NUMEROS AL ARRAY
        public static void ingresoNumeros() {
            do {
                System.out.println("[+] Ingrese Número Entero #" + contador + "\n[Para salir ingrese 0]");
                capturador = scanner.nextLine();
                if(!isNumeric(capturador)){
                    System.out.println("[ERROR] Ingrese sólo valores Numéricos");
                }else if(capturador.trim().length() == 0){
                    System.out.println("[ERROR] No puede estar vacío");
                }else if(listaNumeros.size() < 3 && Integer.parseInt(capturador)==0){
                    System.out.println("[ERROR] No puede salir, a menos que haya ingresado 3 número enteros");
                }else if(Integer.parseInt(capturador)!=0){
                    //CONDICIÓN QUE SE CUMPLE CUANDO SE CUMPLEN TODAS LA VALIDACIONES
                    guardarNumero(Integer.parseInt(capturador));
                }
            }while(!isNumeric(capturador)
                    || capturador.trim().length()==0
                    || Integer.parseInt(capturador)!= 0
                    || listaNumeros.size()<3
                    );
    
        }
    
        //FUNCIÓN QUE GUARDA EL NUMERO DENTRO DEL ARRAYLIST
        public static void guardarNumero(int capturador) {
            listaNumeros.add(capturador);
            contador++;
            System.out.println(listaNumeros);
            System.out.println(listaNumeros.size());
        }
    
        //FUNCION QUE CALCULA EL PROMEDIO SIMPLE
        public static double calculaPromedio(ArrayList<Integer>listaNumeros) {
            double promedio;
            int suma = 0;
            for(int i = 0; i < listaNumeros.size(); i++) {
                suma += listaNumeros.get(i);
            }
            promedio = suma /listaNumeros.size();
            return promedio;
        }
    
        //FUNCION QUE DEVUELVE NUMERO MAX
        public static int calculaNumMax(ArrayList<Integer>listaNumeros) {
            int numMax;
            numMax = Collections.max(listaNumeros);
            return numMax;
        }
    
        //FUNCION QUE DEVUELVE NUMERO MIN
        public static int calculaNumMin(ArrayList<Integer>listaNumeros) {
            int numMin;
            numMin = Collections.min(listaNumeros);
            return numMin;
        }
    
        //FUNCION PARA ELIMINAR NÚMERO PARES
        public static void eliminaNumPares(ArrayList<Integer>listaNumeros) {
            for(int i = 0; i < listaNumeros.size(); i++) {
                if(listaNumeros.get(i)%2==0) {
                    listaNumeros.remove(i);
                    i--;
                }
            }
        }
    
    
        //FUNCION QUE DEVUELVE TRUE EN CASO DE QUE LA CADENA SE PUEDA CONVERTIR A NÚMERO
        private static boolean isNumeric(String cadena){
            try{
                Integer.parseInt(cadena);
                return true;
            }catch(NumberFormatException nfe){
                return false;
            }
        }
    }
