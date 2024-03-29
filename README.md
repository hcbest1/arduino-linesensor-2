# arduino-linesensor-2

#define ledPin 13  // LED는 디지털 핀 13에 연결됨
#define LINE_DETECT_WHITE 1

int linesensor_data[5] = {0, 0, 0, 0, 0};
int linesensor_pin[5] = {2, 3, 4, 5, 6};

int read_digital_line_sensor(void)
{
  int i;
  int sum = 0;
  for(i=0;i<5;i++)
  {
    if(LINE_DETECT_WHITE == 0)
    {
      linesensor_data[i] = 1 - digitalRead(linesensor_pin[i]);
    }
    else
    {
      linesensor_data[i] = digitalRead(linesensor_pin[i]);
    }
    sum += linesensor_data[i];
  }
  return sum;
}

void setup() {
  int i;
  pinMode(ledPin, OUTPUT);
  for(i=0;i<5;i++)
  {
    pinMode(linesensor_pin[i], INPUT);
  }
  Serial.begin(9600);
}
