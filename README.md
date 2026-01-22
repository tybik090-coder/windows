import javax.swing.*;
import java.awt.*;

public class Main extends JFrame {

    private int percent = 0;
    private JLabel percentLabel;
    private Timer timer;

    public Main() {
        setUndecorated(true);
        setExtendedState(JFrame.MAXIMIZED_BOTH);
        setDefaultCloseOperation(EXIT_ON_CLOSE);
        getContentPane().setBackground(new Color(0, 120, 215));
        setLayout(null);

        JLabel face = new JLabel(":(");
        face.setForeground(Color.WHITE);
        face.setFont(new Font("Segoe UI", Font.PLAIN, 120));
        face.setBounds(120, 80, 300, 150);
        add(face);

        JLabel text = new JLabel("<html>Your PC ran into a problem and needs to restart.<br>We're just collecting some error info.</html>");
        text.setForeground(Color.WHITE);
        text.setFont(new Font("Segoe UI", Font.PLAIN, 28));
        text.setBounds(120, 230, 1200, 100);
        add(text);

        percentLabel = new JLabel("0% complete");
        percentLabel.setForeground(Color.WHITE);
        percentLabel.setFont(new Font("Segoe UI", Font.PLAIN, 26));
        percentLabel.setBounds(120, 340, 400, 60);
        add(percentLabel);

        setVisible(true);

        timer = new Timer(50, e -> updatePercent());
        timer.start();
    }

    private void updatePercent() {
        percent++;
        percentLabel.setText(percent + "% complete");

        if (percent >= 100) {
            timer.stop();
            new Timer(800, e -> System.exit(0)).start();
        }
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(Main::new);
    }
}




