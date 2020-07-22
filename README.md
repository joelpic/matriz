#define shcp re0_bit
#define ds   re1_bit
#define stcp re2_bit

#define texto  62 //140max
#define espaco 60 //max 105

int correr; // contador do longo do texto
int velocidade; //velocidade da rolagem
int multiplexacao;// contador de multiplexacao de coluna

int const filas[texto+espaco]={0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
0, 58, 73, 46, 0, 62, 73, 65, 0, 6, 1, 1, 126, 0, 63, 72, 72, 63, 0, 0, 0, 0, 127, 73, 73, 62, 0, 62, 73, 65, 0, 63, 64, 48, 64, 63,
0,0,0,0,0, 126, 1, 1, 126, 0, 127, 0, 127, 32, 16, 127, 0, 127, 65, 34, 28, 0, 62, 65, 65, 62,
};

unsigned char  coluna []={1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40};

 void main()

 {

 ansel=0;
  anselh=0;

  C1ON_bit = 0;                     
  C2ON_bit = 0;

  trise=0x00;
  porte=0x00;

  trisa=0x00;
  porta=0b00000000;

  trisb=0b11110001;
  portb=0b00000000;

  trisc=0x00;
  portc=0b00000000;

  trisd=0x00;
  portd=0x00;

while(1)
{
 for(correr=0;correr<texto+20;correr++)
   {
        for(velocidade=0;velocidade<3;velocidade++)
        {
          for(multiplexacao=0;multiplexacao<40;multiplexacao++)
          {
          
          if (coluna[multiplexacao] == 1)
          {
          ds = 1;
          } else 
          {
          ds = 0;
          }
          shcp=0;
          shcp=1;
          stcp=1;
          stcp=0;

          portc=0;
          portc=(~filas[correr+multiplexacao]);
          delay_ms(1);
        }
   }
  }
 }
}
