# WordPress-Custom-Post-Types-Loop
<?php
$args = array(
    'post_type' => 'Post Name',
    'posts_per_page' => -1,
    'order' => 'ASC',
    'category_name' => 'Category name'
);
$the_query = new WP_Query( $args ); ?>

<?php if ( $the_query->have_posts() ) : ?>
    <div class="Slider-container">
        <?php while ( $the_query->have_posts() ) : $the_query->the_post(); ?>
            <div class="Slider">						
                <?php if ( get_the_post_thumbnail() ) : /* Show the featured image if there have it */ ?>									 
                    <?php the_post_thumbnail(); ?>
                <?php endif; ?>
                <h2><?php the_title(); ?></h2>
                <?php the_content(); ?>
            </div>
        <?php endwhile; ?>
    </div>

    <?php wp_reset_postdata(); ?>

<?php endif; ?>
