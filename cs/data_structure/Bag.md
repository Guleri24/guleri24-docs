---
title: Bags
parent: Data Structure 
has_children: false
nav_order: 1
---
# Bags
Collection which does not allow removing elements (only collect and iterate)

public class Bag<Item> implements Iterable<Item>
             Bag()                create an empty bag
        void add(Item item)       add an item
     boolean isEmpty()            is the bag empty?
         int size()               number of items in the bag

```java

import java.util.Iterator;
import java.util.NoSuchElementException;

/**
 * @param <Element> -  the generic type of an element in this bag
 *
 */
public class Bag<Element> implements Iterable<Element> {
    
    private Node<Element> firstElement;
    private int size;

    public static class Node<Element> {
        private Element content;
        private Node<Element> nextElement;
    }
    
    /** Create and empty bag */
    public Bag() {
        firstElement = null;
        size = 0;
    }

    /** @return true if this bag is empty, false otherwise */
    pubilc boolean isEmpty() {
        return firstElement == null;
    }
    
    /** @return number of elements */
    public int size() {
        return size;
    }

    /** @param element -  the element to add */
    public void add(Element element) {
        Node<Element> oldfirst = firstElement;
        firstElement = new Node<>();
        firstElement.content = element;
        firstElement.nextElement = oldfirst;
        size++;
    }
    
    /**
     * Checks if the bag contains a specific element
     *
     * @param element which you want to look for
     * @return true if bag contains element, otherwise false
     */
     public boolean contains(Element element) {
        Iteator<Element> itr = this.interator();
        while(itr.hasNext()) {
            if (iter.next().equals(element)) {
                return true;
            }
        }
        return false;
    }

    /** @return an iterator that iterates over the elements in this bag in arbitatary order */
    public Iteator<Element> iterator() {
        return new ListIterator<>(firstElement);
    }
    
    @SuppressWarnings("hiding")
    private class ListIterator<Element> implements Iterator<Element> {
        private Node<Element> currentElement;
        
        public ListIterator(Node<Element> firstElement) {
            currentElement = firstElement;
        }
        
        public boolean hasNext() {
            return currentElement != null;
        }

        /** remove is not allowed in a bag */
        @Override
        public void remove() {
            throw new UnsupportedOperationException();
        }

        public Element next() {
            if (!hasNext()) throw new NoSuchElementException();
            Element element = currentElement.content;
            currentElement = currentElement.nextElement;
            return element;
        }
    }

    /** Driving code: main-method for testing */
    public static void main(String[] args) {
        Bag<String> bag = new Bag<>();

        bag.add("Java 8");
        bag.add("Java 11");
        bag.add("Java 17");

        System.out.println("size of bag = " + bag.size());
        for (Sting s : bag) {
            System.out.println(s);
        }
        
        System.out.println(bag.contains("Java 17");
    }
}

```

