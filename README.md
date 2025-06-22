# Billingimport javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class CafeBillingSystem extends JFrame implements ActionListener {

    JTextField coffeeQty, sandwichQty, cakeQty;
    JTextArea billArea;
    JButton generateBtn, clearBtn;

    CafeBillingSystem() {
        setTitle("☕ Café Billing System");
        setSize(400, 500);
        setDefaultCloseOperation(EXIT_ON_CLOSE);
        setLayout(null);

        JLabel title = new JLabel("Café Menu");
        title.setFont(new Font("Poppins", Font.BOLD, 24));
        title.setBounds(130, 20, 200, 30);
        add(title);

        JLabel coffee = new JLabel("Coffee (₹80):");
        coffee.setBounds(50, 80, 120, 25);
        add(coffee);
        coffeeQty = new JTextField("0");
        coffeeQty.setBounds(200, 80, 100, 25);
        add(coffeeQty);

        JLabel sandwich = new JLabel("Sandwich (₹120):");
        sandwich.setBounds(50, 120, 120, 25);
        add(sandwich);
        sandwichQty = new JTextField("0");
        sandwichQty.setBounds(200, 120, 100, 25);
        add(sandwichQty);

        JLabel cake = new JLabel("Cake Slice (₹60):");
        cake.setBounds(50, 160, 120, 25);
        add(cake);
        cakeQty = new JTextField("0");
        cakeQty.setBounds(200, 160, 100, 25);
        add(cakeQty);

        generateBtn = new JButton("Generate Bill");
        generateBtn.setBounds(50, 210, 120, 30);
        generateBtn.addActionListener(this);
        add(generateBtn);

        clearBtn = new JButton("Clear");
        clearBtn.setBounds(200, 210, 100, 30);
        clearBtn.addActionListener(this);
        add(clearBtn);

        billArea = new JTextArea();
        billArea.setBounds(50, 260, 280, 160);
        billArea.setFont(new Font("Monospaced", Font.PLAIN, 12));
        add(billArea);

        setVisible(true);
    }

    public void actionPerformed(ActionEvent e) {
        if (e.getSource() == generateBtn) {
            int coffee = Integer.parseInt(coffeeQty.getText());
            int sandwich = Integer.parseInt(sandwichQty.getText());
            int cake = Integer.parseInt(cakeQty.getText());

            int total = (coffee * 80) + (sandwich * 120) + (cake * 60);

            billArea.setText("        Café Receipt\n");
            billArea.append("==========================\n");
            billArea.append("Coffee     x " + coffee + " = ₹" + (coffee * 80) + "\n");
            billArea.append("Sandwich   x " + sandwich + " = ₹" + (sandwich * 120) + "\n");
            billArea.append("Cake Slice x " + cake + " = ₹" + (cake * 60) + "\n");
            billArea.append("--------------------------\n");
            billArea.append("Total: ₹" + total + "\n");
            billArea.append("==========================");
        } else if (e.getSource() == clearBtn) {
            coffeeQty.setText("0");
            sandwichQty.setText("0");
            cakeQty.setText("0");
            billArea.setText("");
        }
    }

    public static void main(String[] args) {
        new CafeBillingSystem();
    }
}
