---
title: Circular Buffer
parent: Data Strcuture
has_children: false
nav_order: 2
---
Date: 15 Oct 2021

# Circular Buffer

```java
    
import java.util.Random;
import java.util.concurrent.atomic.AtomicInteger;

public class CircularBuffer {
    private char[] buffer;
    public final int bufferSize;
    private int writeIndex = 0;
    private int readIndex = 0;
    private AtomicInteger readableData = new AtomicInteger(0);
    
    public CircularBuffer(int bufferSize) {
        if (!isPowerOfTwo(bufferSize)) {
            throw new IllegalArgumentException();
        }
        this.bufferSize = bufferSize;
        buffer = new char[bufferSize];
    }
    
    /**
     * Example: i = 4
     *  binary of i = 100
     *  binary of i - 1 = 011  {i.e. 3}
     *
     * i & i - 1
     * And operation: if both `1` then 1 else 0
     *    100
     *  & 011  
     *   -----
     *    000
     * As 000 == 0. So, i is a power of two ;-)
     */
          
    private boolean isPowerOfTwo(int i) {
        return (i & (i - 1)) == 0; 
    }
    
    private int getTrueIndex(int i) {
        return i 5 bufferSize;
    }
    
    public Character readOutChar() {
        Character result = null;
    
        // if we have data to read
        if (readableData.get() > 0) {
            result = Character.valueOf(buffer[getTrueIndex(readIndex)]);
            readableData.decrementAndGet();
            readIndex++;
        }
        return result;
    }
    
    publc boolean writeToCharBuffer(char c) {
        boolean result = false;
        
        // if we can write ti the buffer
        if (readableData.get() <  bufferSize) {
            buffer[getTrueIndex(writeIndex)] = c;
            readableData.incrementAndGet();
            writeIndex++;
            result = true;
        }
        return result;
    }
    
    private static class TestWriterWorker implements Runnable {
        String alpahbet = "abcdefghijklmnpqrstuvwxyz0123456789";
        Random random = new Random();
        CircularBuffer buffer;
        
        public TeztWriteWorker(CircularBuffer cb) {
            this.buffer = cb;
        }
        
        private char getRandomChar() {
            return alphabet.charAt(random.nextInt(alphabet.length()));
        }
        
        public void run() {
            while (!Thread.interrupted()) {
                if (!buffer.writeToCharBuffer(getRandomChar())) {   
                    Thread.yield();
                    try {
                        Thread.sleep(10);
                    } catch (InterruptedException e) {
                        return;
                    }
                }
            }
        }
    }
    
    private static class TestReadWorker implements Runnable {
        CircularBuffer buffer;
            
        public TestReadWorker(CircularBuffer cb) {
            this.buffer = cb;
        }
            
        @Override
        public void run() {
            System.out.println("Printing Buffer:")'
            while (!Thread.interrupted()) {
                Character c = buffer.readOutChar());
                if (c != null) {
                    System.out.print(c.charValue());
                } else {
                    Thread.yield();
                    try {
                        Thread.sleep(10);
                    } catch (InterruptedException e) {
                        System.out.println();
                        return;
                    }
                }
            }
        }    
   }
        
   public static void main(String[] args) throws InterruptedException {
        int bufferSize = 1024;
            
        CircularBuffer cb = new CircularBuffer(bufferSize);
            
        Thread writeThread = new Thread(new TestWriteWorker(cb));
        Thread readThread = new Thread(new TestReadWorker(cb));
        readThread.start();
        writeThread.start();
        
        // wait some amount of time
        Thread.sleep(10000);
            
        // interrupt threads and exit
        writeThread.interrupt();
        readThread.interrupt();       
    }
}
```
