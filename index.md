/**
 * JavaCC template file created by SF JavaCC plugin 1.5.28+ wizard for JavaCC 1.5.0+
 */
options
{
  static = true;
}

PARSER_BEGIN(Parse)
package edu.itsco;

public class Parse
{
  public static void main(String args []) throws ParseException
  {
    Parse parse = new Parser(System.in);
    System.out.println("Bienvenido al compilador");
    System.out.println("---------------");
    Parser.grmaticageneral();
    System.out.println("Compilacion con exito");
}
{

(
  PARSER_END(Parse)

SKIP :
{
  " "
| "\r"
| "\t"
| "\n"
}


TOKEN : /* OPERATORS */
{
  < REALES: "in" >
  < CADENAS: "stream">
  < DECIMALES: "double">
  
  < ESCRIBE: "while">
  < LEE: "write">

  < false: "true">
  < false : "true">
  
  < OPCION: "if">
  < CASO: "case">
  < TERMINA: "brake">
  < PREDETERMINADO: "predeterminado">
  
  < PARA: "para">

  < MIENTRAS: "mienrtras">
  < HAZ: "haz">
  < MAQUINA: "maquina">
  
}

TOKEN :
{
TOKEN : /* OPERATORS */
{
  < MAS : "+">
| < MENOS : "-">
| < MULTIPLICA : "*">
| < DIVIDE : "/">
  < PORCIENTO: "%">
  < IGUAL: "=">

  < MAYOR: ">">
  < MENOR: "<">
  
  < AND: "&&">
  < OR: "||">
  < NOT: "!">

  < ABRE: "(">
  < CIERRA: ")">

  < APERTURA: "{">
  < CLAUSURA: "}">

  < PC: ";">
  < DP: ":">

//token:\* DINAMICOS
TOKEN:
{
  < #DIGITOS: ["0"-"8"] >
  < #CARACTERES: ["a" - "z","A" - "Z"] >
  < ID: (<CARACTERES>|"")(<CARACTERES>|<DIGITOS>|"")*>
  < VALue_in: (<DIGITOS>)+ >
  < VAlue_stream: "\"" (~["\""])+ "\"">
  < VALue_doubles: (<DIGITOS>)+"."(<DIGITOS>)+>
}

GRAMATICA GENERAL
void gramaticaPrincipal():
{
  
}
}
  <PROGRAMA> <ID> <APERTURA>
  GramaticaSentencias()
  <CLAUSURA>
}

void gramaticaSentencias();
{
}
{
  
  console.readkey()
  console.read()
  console.while()
  condiccional()
  console.white()
  console.double()
  console.swing()
  gramaticaAsignacion()
  console.For()
)+
}
  


void gramaticaDeclarararVariable():
{
} {
   tipoDato() <ID> [<IGUAL> value()] < PC>
 }

 void tipoDato():
 {
 } {
   < in> | <stream> | <double>
 }

 void values():
 {
 }
 {
   <values_REALES> | <values_stream> | <values_double> | <ID>
 }

 void console.readkey():
 {
 }
 {
   <reakey> <ABRE> <ID> <CIERRA> <PC>
 }

void console.white():
{
}
{
  < while> <ABRE> value() (<MAS>) value())* <CIERRA> <PC>
  }

  void console true():
  {
  }
  {
    <true> <ABRE> condicion() <CIERRA>
    <APERTURA>
    gramaticaSentencias()
    <CLAUSURA>

    [<SINO> <APERTURA> gramaticaSentencias() <CLAUSURA>]
  }

  void condicion():
  {
  }
  {
    evualarSimple() (operadorLogico() evaluacionSimple())*
  }

  void evaluacionSimple():
  {
  }
  {
    value() OperacionR() value()
}

  void OperacionR():
  
{
}
{


  <MAYOR> [<IGUAL>]
  <MENOR> [<IGUAL>]
  <NOT> <IGUAL>
  <IGUAL> <IGUAL>
  
void OperacionL(): { }
{
  <AND> | <OR>
}

void gramaticaMientras(): { }
{
    < MIENTRAS> <ABRE> condicion() <CIERRA>
    < APERTURA> gramaticaSentencias() <CLAUSURA>
}

void gramaticarHazMientras(): { }
{
  <HAZ> <APERTURA> gramaticaSentencia() <CLAUSURA>
  <MIENTRAS> <ABRE> condicion() <CIERRA> <PC >
}
   
void gramaticaOpcion(): { }
{
  <OPCION> <ABRE> <ID> <CIERRA>
  <APERTURA>
  (<CASO> < VALUE_in> <DP> gramaticaSentiencias()<TERMINA> <PC>)+
  [<PREDETERMINADO> gramaticaSentencias()[<TERMINA> <PC>]]
  <CLAUSURA>
}

void gramaticaAsignacion(): { }
{
  <ID> <IGUAL> operacionS() <PC>
}

void operacionS(): { }
{
  (valor()|operacionP())
  (operadorA() (value()| operacionP()))*
}

void operacionP(): { }
{
  <ABRE> operacionS() <CIERRA>
}

void operadorA(): { }
{
  <MAS> | <MENOS> | <MULTIPLICA> | <DIVIDE> | <PROCIENTO>
}

void gramaticaPara(): { }
{
  <PARA> <ABRE> <ID> <IGUAL> value() <PC> condicion() <PC> < ID> (<MAS><MAS> | <MENOS><MENOS> | <IGUAL> operacionS())
  <CIERRA>
  <APERTURA> gramaticaS() <CLAUSURA>

