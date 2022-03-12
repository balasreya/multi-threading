# multi-threading
import java.util.Random;
class Thread1 extends Thread
{
    int i,n;
    Random r=new Random();
    public void run()
    {
        for(i=0;i<5;i++)
        {
            int n=r.nextInt(10);
            System.out.println("Thread1 generates Thread");
            if(n%2==0)
            {
                Thread2 t2=new Thread2(n);
                t2.start();
            }
            else
            {
                Thread3 t3=new Thread3(n);
                t3.start();
            }
        }
    }
}
class Thread2 extends Thread
{
    int n;
    Thread2(int n)
    {
        this.n=n;
    }
    public void run()
    {
        System.out.println("Thread2 is extened and generated:"+n*n);
    }
}
class Thread3 extends Thread
{
    int n;
    Thread3(int n)
    {
        this.n=n;
    }
    public void run()
    {
        System.out.println("Thread3 is executed and generated:"+n*n*n);
    }
}
class Main
{
    public static void main(String args[])
    {
        Thread t1=new Thread1();
        t1.start();
    }
}

