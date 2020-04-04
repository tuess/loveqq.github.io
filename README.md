# tuess.github.io
# java 创建并写入文件
        File file = new File("D:\\Desktop\\data.txt");
        if (!file.exists()) {
            System.out.println("文件不存在!");
            file.createNewFile();
        }
        Scanner scanner = new Scanner(System.in);
        while (scanner.hasNext()) {
            String data = scanner.nextLine();
            List<Term> result = HanLP.segment(data);
            try {
                FileWriter writer = new FileWriter(file);
                BufferedWriter out = new BufferedWriter(writer);
                for (Term term : result) {
                    System.out.println(term);
                    out.write(term.toString()+" ");
                    out.flush();
                }
                out.close();
            }catch (Exception e){
                e.printStackTrace();
            }
        }
