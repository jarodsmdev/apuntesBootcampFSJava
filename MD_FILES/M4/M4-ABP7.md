# M4-ABP7

---

    package m4ABP7;
    import javax.swing.JOptionPane;

    public class M4ABP7 {
        //DECLARACIÓN DE VARIABLES GLOBALES
        static int vocales = 0;
        //DECLARAR E INICALIZAR ARRAY DE VOCALES
        public static char[] arrVocales = new char[] {'a', 'e', 'i', 'o', 'u'};

        static int consonantes = 0;
        //DECLARAR E INICIALIZAR ARRAY DE CONSONANTES
        public static char[] arrConsonantes = new char[] {'b', 'c', 'd', 'f', 'g', 'h', 'j', 'k', 'l', 'm', 'n', 'ñ', 'p', 'q', 'r', 's', 't', 'v', 'w', 'x', 'y', 'z'};

        //DECLARAR VARIABLE STRING PARA RECIBIR EL TEXTO DE LOS INPUTS/PROMP
        static String capturador = "";

        public static void main(String[] args) {
            // TODO Auto-generated method stub
            //BLOQUE DO WHILE PARA VALIDACIONES NULL O VACÍO
            do {
                capturador = JOptionPane.showInputDialog("Ingrese Texto a analizar");
                if(capturador == null) {
                    System.out.println("**Ha presionado Cancelar**\nPrograma Finalizado");
                    System.exit(0);
                }else if(capturador.length()==0) {
                    System.out.println("[ERROR] No puede estar vacío, por favor ingrese un texto y vuelva a intentar.");
                }
            }while(capturador == null || capturador.length()==0);

            //EJECUCIÓN NORMAL PASANDO LAS VALIDACIONES
                capturador = capturador.trim();
                ValidaCadena(capturador);
                MostrarResultados(vocales, consonantes);

        }

        //FUNCIÓN PARA CONTAR TANTO VOCALES COMO CONSONANTES Y VOLCAR SU RESULTADO A VARIABLES GLOBALES
        public static void ValidaCadena(String cadenaTexto) {
            for(int i = 0; i < cadenaTexto.length(); i++) {
                //FOR PARA VALIDAR VOCALES
                for(int j = 0; j < arrVocales.length; j++) {
                    if(cadenaTexto.toLowerCase().charAt(i)==arrVocales[j]) {
                        vocales++;
                        break;
                    }
                }
                //FOR PARA VALIDAR CONSONANTES
                for(int k = 0; k < arrConsonantes.length; k++) {
                    if(cadenaTexto.toLowerCase().charAt(i)==arrConsonantes[k]) {
                        consonantes++;
                        break;
                    }
                }
            }
        }

        //FUNCIÓN PARA MOSTRAR EN PANTALLA LOS RESULTADOS
        public static void MostrarResultados(int TotalVocales, int TotalConsonantes) {
            System.out.println("LUEGO DE HABER ANALIZADO LA PALABRA:\n'" + capturador + "'\n");
            System.out.println("PODEMOS INDICAR LO SIGUIENTE:");
            System.out.println("CANTIDAD DE VOCALES: " + vocales);
            System.out.println("CANTIDAD DE CONSONANTES: " +  consonantes);
        }

    }
