# M4-ABP8

---

    package m4ABP8;
    import java.util.Scanner;
    import java.util.ArrayList;

    public class M4ABP8 {
        //VARIABLES AUXILIARES GLOBALES
        static String capturadorNombre = "";
        static String capturadorNota = "";
        static int contador = 1;

    //OBJETO SCANNER
    static Scanner scanner = new Scanner(System.in);

    //ARRAYLIST PARA ALMACENAR DATOS INGRESADOS POR USUARIO
    static ArrayList<String> listaAlumno = new ArrayList<String>();
    static ArrayList<Integer> listaNota = new ArrayList<Integer>();

    public static void main(String[] args) {
        // TODO Auto-generated method stub
        pedirNombre();
        mostrarContenido(listaAlumno,listaNota);
        promedioCurso(listaNota);
        //mostrarNotaMaxNombre(listaAlumno, listaNota);
        String mensaje = mostrarNotaMinNombre(listaAlumno, listaNota, mostrarNotaMaxNombre(listaAlumno, listaNota));
        System.out.println(mensaje);
    }

    //FUNCIÓN SOLICITA DATOS NOMBRE Y VALIDA SU INGRESO AL ARRAY listaAlumno
    public static void pedirNombre() {
        do {
            System.out.println("[+]Nombre del Alumno #" + contador +"\n['SALIR' PARA TERMINAR]");
            capturadorNombre = scanner.nextLine();

            if (capturadorNombre == null) { 
                System.out.println("Se ha cancelado el ingreso de nombre");
            }else if(isNumeric(capturadorNombre)) {
                System.out.println("[ERROR] Un nombre al menos debe contener una letra");
            }else if(capturadorNombre.trim().length()==0) {
                System.out.println("[ERROR] No puede estar vacío.");
            }else if(capturadorNombre.equals("SALIR") && listaAlumno.size()<1){
                System.out.println("[ERROR] No puede Salir, debe ingresar a lo menos un alumno y su nota");
            }else if(capturadorNombre.equals("SALIR")) {
                System.out.println("**RESULTADOS**");
            } else {
                //SI EL NOMBRE ES VÁLIDO LLAMA A PEDIRNOTA PARA EL INGRESO
                //System.out.println("NOMBRE: " + capturadorNombre); //DEBUG*****
                pedirNota();
            }
            }while(capturadorNombre.trim().length()==0
                    || capturadorNombre == null
                    || listaAlumno.size()<1
                    || !capturadorNombre.equals("SALIR")
                    || isNumeric(capturadorNombre)
                    );
    }

    // GUARDA LOS DATOS EN EL ARRAY CUANDO PASAN TODAS LAS VALIDACIONE Y SUMA 1 AL CONTADOR
    public static void guardarNombreYNota() {
        listaAlumno.add(capturadorNombre);
        listaNota.add(Integer.parseInt(capturadorNota));
        contador++;
    }

    //FUNCIÓN SOLICITA DATOS CALIFICACIONES Y VALIDA SU INGRESO AL ARRAY listaNota
    public static void pedirNota() {
        do {
            System.out.println("[+]Nota alumno #" + contador + "("+ capturadorNombre +")");
            capturadorNota = scanner.nextLine();
            if (capturadorNota == null) { 
                System.out.println("Se ha cancelado el ingreso de Nota");
            }else if(capturadorNota.length()==0) {
                System.out.println("[ERROR] No puede estar vacío.");
            }else if(!isNumeric(capturadorNota)){
                System.out.println("[ERROR] Sólo caracteres numéricos");
            }else if(!capturadorNota.matches("^[1-7]$")){
                System.out.println("[ERROR] Nota ingresada no es válida [1 - 7]");
            }else {
                //VALIDACIÓN CORRECTA GUARDA LOS DATOS EN EL ARRAY
                //System.out.println("NOTA: "+capturadorNota); //DEBUG*************
                guardarNombreYNota();
            }
        }while(capturadorNota.length()== 0
                || capturadorNota == null
                || !capturadorNota.matches("^[1-7]$")
                );
    }
    //FUNCIÓN PARA CALCULAR PROMEDIO
    static int nota = 0;
    static double promedio = 0;
    private static void promedioCurso(ArrayList<Integer>listaNota) {
        for(int i = 0; i < listaNota.size();i++) {
            nota += listaNota.get(i);
        }
        promedio = nota / listaNota.size();
        System.out.println("Promedio del Curso: " + promedio);
    }

    //FUNCION PARA CALCULAR NOTA MAXIMA Y EL NOMBRE DEL ALUMNO
    private static int mostrarNotaMaxNombre(ArrayList<String>listaAlumno, ArrayList<Integer>listaNota) { 
        int notaMax = 0;
        String nombreMax = "";
        for(int i = 0; i < listaAlumno.size();i++) {
            if(notaMax <= listaNota.get(i)) {
                notaMax = listaNota.get(i);
                nombreMax = listaAlumno.get(i);
            }
        }
        System.out.println(nombreMax + " Obtuvo máxima calificación con: " + notaMax);
        return notaMax;
    }
    //FUNCION PARA CALCULAR NOTA MINIMA Y EL NOMBRE DEL ALUMNO
    private static String mostrarNotaMinNombre(ArrayList<String>listaAlumno, ArrayList<Integer>listaNota, int notaMax) {
        String mensaje = "";
        int notaMin = 0;
        String nombreMin = "";
        for(int i = 0; i < listaAlumno.size(); i++) {
            if(notaMax >= listaNota.get(i)) {
                notaMin = listaNota.get(i);
                nombreMin = listaAlumno.get(i);
            }
        }
    
        mensaje = "" + nombreMin + " obtuvo la calificaión mínima de: " + notaMin;
        return mensaje;
    }


    //FUNCIÓN PARA MOSTRAR ARRAY POR CONSOLA
    private static void mostrarContenido(ArrayList<String>listaAlumnos, ArrayList<Integer>listaNota) {
        System.out.println(listaAlumno); //DEBUG*****
        System.out.println(listaNota); //DEBUG*****
        for(int i = 0; i < listaAlumnos.size(); i++) {
            System.out.println("Nombre Alumno #"+(i+1) + ": " + listaAlumnos.get(i) + " Nota: " + listaNota.get(i));
        }
    }

    //FUNCION QUE RETORNA TRUE SI LA CADENA INGRESADA POR ARGUMENTO ES NUMÉRICA
        private static boolean isNumeric(String cadena) {
            try {
                Integer.parseInt(cadena);
                return true;
            } catch (NumberFormatException nfe) {
                return false;
            }
        }
}
