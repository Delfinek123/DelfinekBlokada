# DelfinekBlokada
1.0 

import org.bukkit.entity.Player;
import org.bukkit.event.EventHandler;
import org.bukkit.event.Listener;
import org.bukkit.event.player.PlayerCommandPreprocessEvent;
import org.bukkit.plugin.java.JavaPlugin;

public final class Main extends JavaPlugin implements Listener {
    @Override
    public void onEnable() {
        getLogger().info("Blokada Komend zostala poprawnie uruchomiona!");
        saveDefaultConfig();
        getServer().getPluginManager().registerEvents(this, this);
    }

    @EventHandler
    private void onCMD(PlayerCommandPreprocessEvent e) {
        Player p = e.getPlayer();
        if (!p.hasPermission("blocked.bypass") || !p.isOp()) {
            if (this.getConfig().getList("blocked-commands").contains(e.getMessage())) {
                e.setCancelled(true);
                e.getPlayer().sendMessage("&cKomenda jest zablokowana!");
            }
        }
    }
}


W razie problemów z zapisywaniem można dodać package czyli:

package: <nazwa package>

import org.bukkit.entity.Player;
import org.bukkit.event.EventHandler;
import org.bukkit.event.Listener;
import org.bukkit.event.player.PlayerCommandPreprocessEvent;
import org.bukkit.plugin.java.JavaPlugin;

public final class Main extends JavaPlugin implements Listener {
    @Override
    public void onEnable() {
        getLogger().info("Blokada Komend zostala poprawnie uruchomiona!");
        saveDefaultConfig();
        getServer().getPluginManager().registerEvents(this, this);
    }

    @EventHandler
    private void onCMD(PlayerCommandPreprocessEvent e) {
        Player p = e.getPlayer();
        if (!p.hasPermission("blocked.bypass") || !p.isOp()) {
            if (this.getConfig().getList("blocked-commands").contains(e.getMessage())) {
                e.setCancelled(true);
                e.getPlayer().sendMessage("&cKomenda jest zablokowana!");
            }
        }
    }
}
