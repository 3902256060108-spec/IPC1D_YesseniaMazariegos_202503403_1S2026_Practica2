
    public void mostrarGrafica() {
    if (arr == null || arr.length == 0) return;

    org.jfree.data.category.DefaultCategoryDataset dataset =
            new org.jfree.data.category.DefaultCategoryDataset();

    
    for (int i = 0; i < arr.length; i++) {
        dataset.addValue(arr[i], "Valor", String.valueOf(i));
    }

    org.jfree.chart.JFreeChart chart =
            org.jfree.chart.ChartFactory.createBarChart(
                    "",
                    "",
                    "",
                    dataset
            );

    chart.setBackgroundPaint(new java.awt.Color(10, 20, 40));

    org.jfree.chart.plot.CategoryPlot plot = chart.getCategoryPlot();
    plot.setBackgroundPaint(new java.awt.Color(10, 20, 40));
    plot.setRangeGridlinePaint(java.awt.Color.WHITE);

    
    org.jfree.chart.renderer.category.BarRenderer renderer =
            new org.jfree.chart.renderer.category.BarRenderer() {
        @Override
        public java.awt.Paint getItemPaint(int row, int column) {
            if (estados == null) return new java.awt.Color(0, 170, 255);
            switch (estados[column]) {
                case 1: return java.awt.Color.YELLOW;
                case 2: return java.awt.Color.RED;
                case 3: return java.awt.Color.GREEN;
                default: return new java.awt.Color(0, 170, 255);
            }
        }
    };

    
    renderer.setDefaultItemLabelsVisible(true);
    renderer.setDefaultItemLabelGenerator(
            new org.jfree.chart.labels.StandardCategoryItemLabelGenerator()
    );
    renderer.setDefaultItemLabelFont(new java.awt.Font("Arial", java.awt.Font.BOLD, 12));
    renderer.setDefaultItemLabelPaint(java.awt.Color.WHITE); // ✅ visibles sobre fondo oscuro
    renderer.setDefaultPositiveItemLabelPosition(
        new org.jfree.chart.labels.ItemLabelPosition(
            org.jfree.chart.labels.ItemLabelAnchor.OUTSIDE12,
            org.jfree.chart.ui.TextAnchor.BOTTOM_CENTER
        )
    ); 

    plot.setRenderer(renderer);

    org.jfree.chart.ChartPanel chartPanel = new org.jfree.chart.ChartPanel(chart);
    panelGrafica.removeAll();
    panelGrafica.setLayout(new java.awt.BorderLayout());
    panelGrafica.add(chartPanel, java.awt.BorderLayout.CENTER);
    panelGrafica.revalidate();
    panelGrafica.repaint();
    panelGrafica.setPreferredSize(new java.awt.Dimension(500, 400)); // ancho, alto
    panelGrafica.setMaximumSize(new java.awt.Dimension(500, 400));
}


public void actualizarGrafica() {
    SwingUtilities.invokeLater(() -> {
        mostrarGrafica();
    });
}

