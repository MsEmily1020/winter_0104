## ๐ป ๊ฒฝ์ฃผ ์ํฉ GUI
- ๋ง์ ๋ฐฐํ ํ ๊ฒฝ์ฃผ ์ํฉํด์ ๋ฐฐํ ์ฑ๊ณต ๋ฐ ์คํจํ๋ ํ๋ก๊ทธ๋จ

## โ Project execution period
  - 2022.01.04

## ๐  Development Environment
- MVC (๋ชจ๋ธ-๋ทฐ-์ปจํธ๋กค๋ฌ, modelโviewโcontroller) ์ด์ฉ
- GUI
  
  - Language : `Java 8` 
  - JDK `1.8.0_341`
  - Tool : `Eclipse`

## ๐ Main Composition
- Thread ์ค์ 
- ๊ฐ ๊ฐ์ฒด(๋ง) ๋น ์ฐ๋ ๋ ๋ง๋ค๊ธฐ
  ```java
   for (int i = 0; i < horses.length; i++) {
		HorseThread t = new HorseThread(horses[i], i);
		t.start();
    }

	public class HorseThread extends Thread{
		JLabel lblHorse;
		int randomValue;
		int horseIndex;
		
		public HorseThread(JLabel lblHorse, int horseIndex) {
			this.lblHorse = lblHorse;
			this.horseIndex = horseIndex;
	      }
  ```
- ๊ฐ ๊ฐ์ฒด์ ์์ง์ด๋ ์ ๋๋ฉ์ด์ ์ฐ๋ ๋
  ```java
    while (true) {
				lblHorse.setLocation(lblHorse.getX()+5, lblHorse.getY()); //์ค๋ฅธ์ชฝ์ผ๋ก ์ด๋
				if(lblHorse.getX()>=540) { //๋์ฐฉ์ง์ 
					winnerIndex[index++] = horseIndex;
					if(index == horses.length-1) { //๋ง์ง๋ง ๋ง์ธ์ง
						index = 0;
						for (int i = 0; i < horses.length; i++)
							horses[i].setLocation(0, horses[i].getY()); //์ถ๋ฐ์ง์ ์ผ๋ก ๋ค์ ์ด๋
						btList = new ArrayList<BettingPerson>(); //์๋ก์ด ๋ฐฐํ ์ฌ๋ ๋ค์ ์๋ ฅ ๋ฐ๊ธฐ ์ํด์
					}
					break;
				}
				
				try {
					Random random = new Random();
					sleep(10 * random.nextInt(10)); //์ด๋ํ๋ ์ ๋๋ฉ์ด์(๋๋ค ๋น ๋ฅด๊ธฐ)
				} catch (InterruptedException e) {
					e.printStackTrace();
				}
			}
  ```
