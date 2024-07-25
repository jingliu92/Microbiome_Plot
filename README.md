# ggplot2-barplot
## Barplot with y-axis break
```{r}
clr <- c("#3D5A77","#CD5C55","#3D5A77","#CD5C55","#3D5A77","#CD5C55")
ggplot(BWG_summary, aes(x=Group, y=Mean, fill=Group)) + 
  facet_grid(.~Breed, scales = "free") +
  geom_bar(stat="identity", colour= clr, position=position_dodge(0.6),width = 0.7) +
  geom_errorbar(aes(ymin=Mean, ymax=Mean+SEM),size = 1, width=.3,
                 position=position_dodge(.6),colour = clr) + 
 # geom_text(data = dt, aes(y = quant, label = cld), size = 2.0, vjust=1.2, hjust =0.5)+
   scale_fill_manual(name="Group",values= clr)+
  scale_y_break(breaks = c(70, 170)) + 
  scale_y_continuous(expand = c(0, 0),limits = c(0,420),breaks= c(0,100,200,300,400)) +
   labs(title=NULL,
       x=NULL,
       y="BWG (g)") +
   theme_classic()+ # theme_bw()
   theme(panel.grid.major = element_blank(),
        panel.grid.minor = element_blank(),
        legend.position  = "none",
        plot.title = element_text(hjust = 0.5),
        panel.grid = element_blank(),axis.text.x = element_text(angle = 60, vjust = 0.8, hjust= 0.8),
        text = element_text(size = 10, family = 'Arial'))

ggsave('Figure/BWG.png',
       height = 2.5,
       width = 3.5,
       unit = 'in',
       dpi = 300)
```
