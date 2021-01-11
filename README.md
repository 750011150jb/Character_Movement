import java.util.*;
import java.io.*;
import java.awt.*;
import java.awt.event.*;
import java.awt.Image.*;
import javax.swing.*;
public class TimerTestGood2
{
	public static void main(String args[])throws IOException
	{ 
		Windows myW=new Windows();
		myW.setSize(800,600);
		myW.addWindowListener(new WindowAdapter()
		{
			public void windowCLosing(WindowEvent event)
			{
				System.exit(0);
			}
		});
		myW.show();
	
	
}
}
class Windows extends Frame implements KeyListener
{
	private int x, y, xold, yold, deltaX1, deltaX2, deltaX3, raftX1, raftX2, raftX3;
	private boolean go, move, firsttime, play, playTime, frog;
	private Image dbImage;
	private Graphics dbg;
	public Windows()
	{
		
		x = 390;
		deltaX1=0;
		deltaX2=800;
		deltaX3=0;
		raftX1=0;
		raftX2=800;
		raftX3=0;
		y=560;
		xold=x;
		yold=y;
		firsttime=true;
		go=false;
		play=false;
		move=false;
		playTime=false;
		addKeyListener(this);
	}
	public void paint(Graphics g)
	{
		if(firsttime) 
			play(g);
	}
	public void update(Graphics g)
	{
	
		if (dbImage == null) {
			dbImage = createImage (this.getSize().width, this.getSize().height);
			  dbg = dbImage.getGraphics ();
		}
		dbg.setColor (getBackground ());
		dbg.fillRect (0, 0, this.getSize().width, this.getSize().height);
		dbg.setColor (getForeground());
		paint (dbg);
		g.drawImage (dbImage, 0, 0, this);
	}
	
	public void start(Graphics g)
	{
		if(play) 
			play(g);
		g.setColor(Color.cyan);
		g.fillRect(0,0,800,600);
		g.setColor(Color.black);
		g.setFont(new Font("Courier", Font.BOLD, 40));
		g.drawString("Frogger Game", 200, 60);
		g.setFont(new Font("Courier", Font.BOLD, 20));
		g.drawString("Enter to Play", 100, 80);
		g.drawString("Escape to Exit", 600, 80);
		if(play) 
			play(g);
	}
	public void play(Graphics g) {
		g.setColor(Color.blue);
		g.fillRect(0,60,800,215);
		g.setColor(Color.gray);
		g.fillRect(0,275,800,285);
		g.setColor(Color.black);
		g.fillRect(0,560,800,40);
		g.setColor(Color.green);
		g.fillRect(0,0,800,95);
		
		g.setColor(Color.black);
		g.drawRect(20,465,15,4);
		g.fillRect(20,465,15,4); // FIRST ROW
		g.fillRect(50,465,15,4);
		g.fillRect(80,465,15,4);
		g.fillRect(110,465,15,4);
		g.fillRect(140,465,15,4);
		g.fillRect(170,465,15,4);
		g.fillRect(200,465,15,4);
		g.fillRect(230,465,15,4);
		g.fillRect(260,465,15,4);
		g.fillRect(300,465,15,4);
		g.fillRect(330,465,15,4);
		g.fillRect(360,465,15,4);
		g.fillRect(390,465,15,4);
		g.fillRect(420,465,15,4);
		g.fillRect(450,465,15,4);
		g.fillRect(480,465,15,4);
		g.fillRect(510,465,15,4);
		g.fillRect(540,465,15,4);
		g.fillRect(570,465,15,4);
		g.fillRect(600,465,15,4);
		g.fillRect(630,465,15,4);
		g.fillRect(660,465,15,4);
		g.fillRect(690,465,15,4);
		g.fillRect(720,465,15,4);
		g.fillRect(750,465,15,4);
		g.fillRect(780,465,15,4); // FIRST ROW END
		
		g.fillRect(20,370,15,4); // SECOND ROW
		g.fillRect(50,370,15,4);
		g.fillRect(80,370,15,4);
		g.fillRect(110,370,15,4);
		g.fillRect(140,370,15,4);
		g.fillRect(170,370,15,4);
		g.fillRect(200,370,15,4);
		g.fillRect(230,370,15,4);
		g.fillRect(260,370,15,4);
		g.fillRect(300,370,15,4);
		g.fillRect(330,370,15,4);
		g.fillRect(360,370,15,4);
		g.fillRect(390,370,15,4);
		g.fillRect(420,370,15,4);
		g.fillRect(450,370,15,4);
		g.fillRect(480,370,15,4);
		g.fillRect(510,370,15,4);
		g.fillRect(540,370,15,4);
		g.fillRect(570,370,15,4);
		g.fillRect(600,370,15,4);
		g.fillRect(630,370,15,4);
		g.fillRect(660,370,15,4);
		g.fillRect(690,370,15,4);
		g.fillRect(720,370,15,4);
		g.fillRect(750,370,15,4);
		g.fillRect(780,370,15,4); // SECOND ROW END
		
		Image car1=Toolkit.getDefaultToolkit().getImage("C:\\Users\\Andy\\Pictures\\Random\\MOBILE2RIGHT.jpg");
		Image car2=Toolkit.getDefaultToolkit().getImage("C:\\Users\\Andy\\Pictures\\Random\\MOBILE2.jpg");
		Image car3=Toolkit.getDefaultToolkit().getImage("C:\\Users\\Andy\\Pictures\\Random\\MOBILE2RIGHT.jpg");
		Image raft1=Toolkit.getDefaultToolkit().getImage("C:\\Users\\Andy\\Pictures\\Random\\raft.jpg");
		Image raft2=Toolkit.getDefaultToolkit().getImage("C:\\Users\\Andy\\Pictures\\Random\\raft.jpg");
		Image raft3=Toolkit.getDefaultToolkit().getImage("C:\\Users\\Andy\\Pictures\\Random\\raft.jpg");
		g.setColor(Color.gray);
		frog=true;
		while (frog) {
			
			Image holmesWALK=Toolkit.getDefaultToolkit().getImage("C:\\Users\\Andy\\Pictures\\Random\\holmesWALK.jpg");
			g.drawImage(holmesWALK, x, y, this);
			
		
			try
				{
				  int count = 0;
				  int sleep_time = 2;
				  while (true)
				  {
					Thread.sleep(2);
					count++;
					if (count >=2) 
					{
					g.setColor(Color.gray);
						
					  if(deltaX1>=800)
						  deltaX1=0;
					  if(deltaX2<=-64)
						  deltaX2=800;
					  if(deltaX3/2>=800)
						  deltaX3=0;
						  
					  //RAFTX's
					  if(raftX1/3>=800)
						  raftX1=0;
					  if(raftX2<=-100)
						  raftX2=800;
					  if(raftX3*2>=800)
						  raftX3=0;
						  
					g.drawImage(car1, deltaX1, 300, this);
			   		g.fillRect(deltaX1, 300 ,4, 50);
				   
			   		g.drawImage(car2, deltaX2, 400, this);
			   		g.fillRect(deltaX2+64, 400 ,4, 50);
					
					g.drawImage(car3, deltaX3/2, 500, this);
			   		g.fillRect(deltaX3/2, 500 ,4, 50);
					
					
					//rafts
					g.setColor(Color.blue);
					
					g.drawImage(raft1, raftX1/3, 95, this);
			   		g.fillRect(raftX1/3, 95 ,4, 60);
					
					g.drawImage(raft2, raftX2, 155, this);
			   		g.fillRect(raftX2+100, 155 ,4, 60);
			   		
			   		g.drawImage(raft3, raftX3*2, 215, this);
			   		g.fillRect(raftX3*2, 215 ,4, 60);
			   		
					//rafts end
					
					Thread.sleep(sleep_time);
					repaint();
					break;
					}
					if (count <=5 ) {
					  deltaX1 += 2;
					  deltaX2 -= 2;
					  deltaX3 += 2;
					  raftX1 += 2;
					  raftX2 -= 2;
					  raftX3 +=2;
					  
					}
					else if (count >5 && count <=15)
					 deltaX1 += 2;
					else 
					  deltaX1 +=2;
					repaint();
				  }
				}
				catch(Exception e){}
			 
			 	
		} 
				go=false;
	}
	
		
	public void keyPressed(KeyEvent event)
	{
		switch(event.getKeyCode())
			{
				case KeyEvent.VK_LEFT:if(x>=2) 
										x-=4;
									else
										x-=0;
									play=true;
									break;
				case KeyEvent.VK_RIGHT:if(x<=798) 
										x+=4;
									else
										x+=0;
									play=true;
									break;
				case KeyEvent.VK_UP:if(y<=598)
										y-=4;
									else
										y-=0;
									play=true;
									break;
				case KeyEvent.VK_DOWN:if(y>=2)
									y+=4;
									else	
										y+=0;
									play=true;
									break;
				case KeyEvent.VK_ENTER: 
									
										play=true;
										break;
										
				case KeyEvent.VK_ESCAPE:go=false;
										
										System.exit(0);
										break;
				
			
					
			
	}
	}
	public void keyReleased(KeyEvent event){}
	public void keyTyped(KeyEvent event){}
	public void exit(Graphics g)
	{
		go=false;
	
	}
	
}

	


