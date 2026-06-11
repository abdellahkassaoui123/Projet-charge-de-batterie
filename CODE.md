# Projet-charge-de-batterie


Projet de charge de batterie réaliser en C++ en première STI2D
double _ABVAR_1_Mot = 0.0 ;
double _ABVAR_2_Ucapteur = 0.0 ;
double _ABVAR_3_Ubatterie = 0.0 ;
double _ABVAR_4_V = 0.0 ;


void setup()
{
  Serial.begin(9600);
  pinMode( 10 , OUTPUT);
  pinMode( 9 , OUTPUT);
  pinMode( 8 , OUTPUT);
  pinMode( 7 , OUTPUT);
}

void loop()
{
  _ABVAR_1_Mot = analogRead(0) ;
  Serial.print("mot =");
  Serial.print(_ABVAR_1_Mot);
  Serial.println();
  _ABVAR_2_Ucapteur = ( ( _ABVAR_1_Mot * 5.0 ) / 1023.0 ) ;
  Serial.print("U capteur =");
  Serial.print(_ABVAR_2_Ucapteur);
  Serial.println();
  _ABVAR_3_Ubatterie = ( _ABVAR_2_Ucapteur * 5.0 ) ;
  Serial.print("V_mesure");
  Serial.print(_ABVAR_3_Ubatterie);
  Serial.println();
  _ABVAR_4_V = ( ( _ABVAR_3_Ubatterie -6.12 ) * 100) ;
  Serial.print("V (%)");
  Serial.print(_ABVAR_4_V);
  Serial.println();

  if (( ( ( _ABVAR_4_V ) <= ( 27) ) && ( ( _ABVAR_4_V ) >= ( 21.6 ) )))
  {
    analogWrite(10 , 255);
  }
  else
  {
    analogWrite(10 , 0);
  }
  if (( ( ( _ABVAR_4_V ) < ( 21.6 ) ) && ( ( _ABVAR_4_V ) >= ( 16.2 ) ) ))
  {
    analogWrite(9 , 255);
  }
  else
  {
    analogWrite(9 , 0);
  }
  if (( ( ( _ABVAR_4_V ) < ( 16.2 ) ) && ( ( _ABVAR_4_V ) >= ( 10.8 ) ) ))
  {
    analogWrite(8 , 255);
  }
  else
  {
    analogWrite(8 , 0);
  }
  if (( ( ( _ABVAR_4_V ) < ( 10.8) ) && ( ( _ABVAR_4_V ) >= ( 5.4) ) ))
  {
    analogWrite(7 , 255);
  }
  else
  {
    analogWrite(7 , 0);
  }
  if  (( ( ( _ABVAR_4_V ) < ( 5.4) ) && ( ( _ABVAR_4_V ) >= ( -1.06 ) ) ))
  {
    analogWrite(7 , 255);
    delay( 1000 );
    analogWrite(7 , 0);
    delay( 1000 );
  }
  else
  {
        analogWrite(7 , 0);
  }
  if (( ( ( _ABVAR_4_V ) < (-1.06) ) && ( ( _ABVAR_4_V ) >= ( -500 ) ) ))
  {
    analogWrite(6, 255);
  }
  else
  {
        analogWrite(6 , 0);
  }
  if  (( ( _ABVAR_4_V ) > ( 27 ) ))
  {
    analogWrite(10 , 255);
    delay( 1000 );
    analogWrite(10 , 0);
    delay( 1000 );
  }
  else
  {
        analogWrite(7 , 0);
  }



  }
