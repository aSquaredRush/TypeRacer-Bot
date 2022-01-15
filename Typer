package org.example;

import com.jagrosh.jdautilities.commons.waiter.EventWaiter;
import net.dv8tion.jda.api.EmbedBuilder;
import net.dv8tion.jda.api.JDA;
import net.dv8tion.jda.api.JDABuilder;
import net.dv8tion.jda.api.entities.*;
import net.dv8tion.jda.api.events.message.MessageReceivedEvent;
import net.dv8tion.jda.api.hooks.ListenerAdapter;
import net.dv8tion.jda.api.requests.GatewayIntent;

import javax.security.auth.login.LoginException;
import java.awt.*;
import java.io.*;
import java.nio.file.Path;
import java.time.*;
import java.util.ArrayList;
import java.util.HashMap;
import java.util.HashSet;
import java.util.StringTokenizer;
import java.util.concurrent.TimeUnit;

public class Typer extends ListenerAdapter {

    private static final EventWaiter ew = new EventWaiter();

    static long t1;
    static long t2;
    static HashMap<Long, org.example.Racer> racers = new HashMap<Long, org.example.Racer>();
    public static ArrayList<String> pics = new ArrayList<>();
    static String pathWords = "/Users/pankajchaubey/IdeaProjects/FINAL_TRY/src/main/java/org/example/words";
    static String testString = "";
    int lengthTestString = 0;

    public static void add() {
        pics.add("https://media.discordapp.net/attachments/800851029470085183/877692904963977246/unknown.png?width=640&height=939");
        pics.add("https://media.discordapp.net/attachments/800851029470085183/883182297787027456/8190e0ea-7da2-4f6d-8fd2-6554f5cd59dd.png?width=660&height=938");
        pics.add("https://media.discordapp.net/attachments/800851029470085183/877694718346145792/810qkw1hcFL.png?width=704&height=939");
        pics.add("https://media.discordapp.net/attachments/800851029470085183/877694895886835793/Peter-Griffin-Among-Us.png");
        pics.add("https://media.discordapp.net/attachments/800851029470085183/877741833453699132/3ejmmb.png");
        pics.add("https://static.wikia.nocookie.net/surrealmemes/images/7/7a/Can_u_outpizza_da_hut.png/revision/latest/scale-to-width-down/220?cb=20200112022102");
        pics.add("https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQKcU4BlqoiEMsxnqjfFJ_eBFmOOtiomKKCrA&usqp=CAU");
        pics.add("https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTBjAxwqSYljeXWaKvcKw8LnsgoBdDqifHxFg&usqp=CAU");
        pics.add("https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRgH0MIaAKAf20o_0BCqW4tIZPkr6Xh4V1LKA&usqp=CAU");
        pics.add("https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcS0Mq6ouas9giuMuIcllUWX0V3WYjdNkZ-fYQ&usqp=CAU");
        pics.add("https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTs48Ru8ezgBU3o5iO7r2yKhuav8pl_xkc4Uq6GXY3hb6iG99ZVe4aa5BEgDaolUxZWdxI&usqp=CAU");
        pics.add("https://static0.srcdn.com/wordpress/wp-content/uploads/2020/04/Peter-Griffin-Family-Guy-Featured.jpg");
        pics.add("https://cdn.images.express.co.uk/img/dynamic/78/590x/secondary/Fox-Cartoon-Series-Family-Guy-243925.jpg");
        pics.add("https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSy3Q7dzSlxr_SsDr5JCp78cK0DHTS1XTxrWg&usqp=CAU");
        pics.add("https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSXUgm1dughIwb4tbmOke3siu3CLe9XZaY0aDtw59k7qga-bRdqOYP9tH7pi1J1LCEBJeY&usqp=CAU");
        pics.add("https://pbs.twimg.com/media/EP32SHEXsAAw1zQ.jpg");
        pics.add("https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcT2ALNKV9d66Cwuy4r_HxipQCMpIwJYKOvAIA&usqp=CAU");
        pics.add("https://m.media-amazon.com/images/I/51PWmpP0qUL._AC_.jpg");
        pics.add("https://i.ytimg.com/vi/n9eHtXAHInA/maxresdefault.jpg");
        pics.add("https://vignette.wikia.nocookie.net/r2da/images/5/53/Peter_Griffin_Dancing_Compilation_4_Family_Guy_Funny_Moments/revision/latest/scale-to-width-down/670?cb=20190613071848");
        pics.add("https://images.hindustantimes.com/rf/image_size_800x600/HT/p1/2014/06/05/Incoming/Pictures/1226211_Wallpaper2.jpg");
        pics.add("https://media.discordapp.net/attachments/800851029470085183/879844710875791400/unknown.png");
    }

    public EmbedBuilder embedBuilderBuild() {
        EmbedBuilder ebHelp = new EmbedBuilder();
        ebHelp.setTitle("Help");
        ebHelp.setColor(new Color(220, 20, 60));
        ebHelp.addField("**!help**", "```Takes you to the help embed```", false);
        ebHelp.addField("**!test**", "```Sends a string and starts a timer to measure wpm. Timer will stop when the string is typed back```", false);
        ebHelp.addField("**!stop**", "```Stops current test. Wpm will not be recorded```", false);
        ebHelp.addField("**!wpm**", "```Shows wpm.```", false);
        ebHelp.addField("**!resetWPM**", "```Resets wpm to 0```", false);


        return ebHelp;
    }
    public EmbedBuilder statsEmbedBuilderBuild(Racer racer){
        EmbedBuilder ebStats = new EmbedBuilder();
        ebStats.setTitle("Stats");
        ebStats.setColor(new Color(220, 20, 60));
        ebStats.addField("**Average WPM:**","```"+racer.getWPM()+"```",false);
        ebStats.addField("**Highest WPM:**","```"+racer.highestWPM()+"```",false);
        ebStats.addField("**Total Words:**", "```"+racer.totalWords+"```",false);
        ebStats.addField("**Total Tests:**","```"+racer.totalTests+"```",false);
        ebStats.addField("**Total Time:**","```"+racer.totalTime/1000.0+" seconds!s```",false);
        return ebStats;
    }


    public String randomLine(String filePathWithFileName) throws Exception {

        File file = new File(filePathWithFileName);
        final RandomAccessFile f = new RandomAccessFile(file, "r");
        final long randomLocation = (long) (Math.random() * f.length());
        f.seek(randomLocation);
        f.readLine();
        String randomLine = f.readLine();
        f.close();
        return randomLine;
    }

    public String test(String str) throws Exception{
        int n = 0;
        if (str.equals("s") || str.equals("short")) n = (int) (Math.random() * 11 + 1);
        if (str.equals("m") || str.equals("medium")) n = (int) (Math.random() * 41 + 10);
        if (str.equals("l") || str.equals("large")) n = (int) (Math.random() * 101 + 40);
        StringBuilder sb = new StringBuilder("");
        for (int i = 0; i < n; i++) {
            while (true) {
                String randomWord = randomLine(pathWords);
                if (randomWord.length() <= 6) {
                    sb.append(randomWord + " ");
                    break;
                }
            }

        }
        return sb.toString().trim();
    }

    public static void main(String[] args) throws LoginException, IOException, ClassNotFoundException {
        //Build the damn bot
        JDA jda = JDABuilder.createDefault("ODQ3NTAzNTYxOTU2Nzg2MTk2.YK_BMw.5Et5GHcYcxqQts5ZPb4LcRlPUNs").build();
        JDABuilder builder = JDABuilder.createDefault("ODQ3NTAzNTYxOTU2Nzg2MTk2.YK_BMw.5Et5GHcYcxqQts5ZPb4LcRlPUNs");
        JDABuilder.createLight("ODQ3NTAzNTYxOTU2Nzg2MTk2.YK_BMw.5Et5GHcYcxqQts5ZPb4LcRlPUNs", GatewayIntent.GUILD_MESSAGES, GatewayIntent.DIRECT_MESSAGES).addEventListeners(new Typer(),ew).setActivity(Activity.playing("Type!")).build();

        //Serialization!!!!
        racers = deserialize();
        for (long L : racers.keySet()){
            jda.retrieveUserById(L).queue(System.out::println);
        }

        add();
    }


    public static void serialize(HashMap<Long, org.example.Racer> racers) throws IOException, ClassNotFoundException {
        FileOutputStream fos = new FileOutputStream("Racers");
        ObjectOutputStream oos = new ObjectOutputStream(fos);
        oos.writeObject(racers);
        oos.flush();
        oos.close();
    }
    public static HashMap<Long, org.example.Racer> deserialize() throws IOException, ClassNotFoundException {
        FileInputStream fis = new FileInputStream("Racers");
        ObjectInputStream ois = new ObjectInputStream(fis);
        HashMap<Long, org.example.Racer> serialized_racers = (HashMap<Long, org.example.Racer>) ois.readObject();
        ois.close();
        return serialized_racers;
    }
    @Override
    public void onMessageReceived(MessageReceivedEvent event) {
        if (!event.getAuthor().getName().equals("TypeFaster")) {
            String str = event.getMessage().getContentRaw();
            User user = event.getAuthor();
            long userID = user.getIdLong();
            MessageChannel channel = event.getChannel();
            EmbedBuilder eb = embedBuilderBuild();
            EmbedBuilder ebStats;

            //Typer
            if(str.equals("!stats")){
                ebStats = statsEmbedBuilderBuild(racers.get(userID));
                channel.sendMessageEmbeds(ebStats.build()).queue();
            }
            if (!racers.containsKey(userID)) {
                racers.put(userID, new org.example.Racer(userID));
                try {
                    serialize(racers);
                } catch (IOException | ClassNotFoundException e) {
                    e.printStackTrace();
                }
            }


            if (str.contains("!test")) {
                String typeOfTest = str.substring(6);
                try {
                    testString = test(typeOfTest);
                    lengthTestString = testString.length();
                    t1 = System.currentTimeMillis();
                    channel.sendMessage("\u200C"+testString+"\u200C").queue(message -> ew.waitForEvent(
                            MessageReceivedEvent.class,
                            e -> {
                                if (!e.getChannel().getId().equals(channel.getId())) return false;
                                return e.getAuthor().getIdLong() == user.getIdLong();
                            },
                            e -> {
                                String authorMessage = e.getMessage().getContentRaw();
                                if (authorMessage.equals(testString)) {
                                    t2 = System.currentTimeMillis();
                                    channel.sendMessage("WPM: " + 12 * lengthTestString / (1.0 * (t2 - t1) / 1000)).queue();
                                    channel.sendMessage("Time: " + 1.0 * (t2 - t1) / 1000).queue();
                                    racers.get(userID).updateWPM(lengthTestString/5.0, (t2 - t1));

                                    try { serialize(racers);
                                    } catch (IOException | ClassNotFoundException b) { b.printStackTrace(); }
                                }
                                else channel.sendMessage("WRONG HAHAHAHAH").queue();
                            },
                            90, TimeUnit.SECONDS,
                            () ->{
                                channel.sendMessage("Respond faster fatty").queue();
                            }

                            )
                    );
                } catch (Exception a) {
                    a.printStackTrace();
                }
            }
            if (str.equals("!stop")) {
                t1 = 0;
                channel.sendMessage("Test Ended").queue();
            }
            if (str.contains("!wpm")) {
                if (str.length() == 4) {
                    channel.sendMessage(Double.toString(racers.get(userID).getWPM())).queue();
                } else {
                    StringTokenizer st = new StringTokenizer(str);
                    st.nextToken();
                    long getID = Long.parseLong(st.nextToken());
                    channel.sendMessage(Double.toString(racers.get(getID).getWPM())).queue();
                }

            }
            if (str.equals("!resetWPM")) {
                racers.get(userID).resetWPM();
                channel.sendMessage("WPM Reset").queue();
            }
            try {
                serialize(racers);
            } catch (IOException | ClassNotFoundException e) {
                e.printStackTrace();
            }


            //Peter
            if (str.contains("!peter")) {
                int picNumber = (int) (Math.random() * pics.size());
                channel.sendMessage(pics.get(picNumber)).queue();
            }
            if (str.contains("!shatter")) channel.sendMessage(pics.get(0)).queue();
            if (str.contains("!shanker")) channel.sendMessage(pics.get(1)).queue();


            //Help
            if (str.contains("!help")) {
                channel.sendMessageEmbeds(eb.build()).queue();

            }

        }


    }

}
